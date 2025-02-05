## ArgoCD와 GitLab 연동 가이드

## **개요**

이 문서는 ArgoCD와 GitLab을 연동하여 GitOps 기반의 CI/CD 환경을 구축하는 방법을 설명합니다.

## **사전 요구사항**

- Kubernetes 클러스터 접근 권한
- GitLab 계정
- kubectl CLI 도구
- ArgoCD CLI 도구

## **1. GitLab 개인 접근 토큰 생성**

1. GitLab에 로그인 후 사용자 설정으로 이동
2. "Access Tokens" 메뉴 선택
3. 새로운 토큰 생성:
    - 토큰 이름 설정
    - 필요한 권한 선택 (read_repository, read_api)
    - 만료 기간 설정
    - Create personal access token 클릭
4. 생성된 토큰을 안전한 곳에 보관

## **2. Kubernetes 클러스터 준비**

지원되는 환경:

- AWS EKS
- Google GKE
- Azure AKS
- On-premise Kubernetes

## **3. ArgoCD 설치**

`bash*# ArgoCD 네임스페이스 생성*
kubectl create namespace argocd

*# ArgoCD 설치*
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/ha/install.yaml`

## **4. ArgoCD 접근 설정**

## **API 서버 접근**

`bash*# 포트 포워딩 설정*
kubectl port-forward svc/argocd-server -n argocd 8080:443`

## **초기 설정**

`bash*# 초기 관리자 비밀번호 확인*
kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

*# ArgoCD 로그인 및 비밀번호 변경*
argocd login localhost:8080
argocd account update-password`

## **5. GitLab 저장소 연결**

## **CLI를 통한 연결**

`bashargocd repo add <GITLAB_REPO_URL> --username <USERNAME> --password <PERSONAL_ACCESS_TOKEN>`

## **UI를 통한 연결**

1. Settings > Repositories 이동
2. Connect Repo 클릭
3. 저장소 정보 입력:
    - Repository URL
    - Username
    - Personal Access Token

## **6. 애플리케이션 배포**

## **애플리케이션 생성**

`bashargocd app create <app-name> \
  --repo <GITLAB_REPO_URL> \
  --path <PATH_TO_MANIFEST> \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace <NAMESPACE>`

## **동기화 설정**

`bash*# 수동 동기화*
argocd app sync <app-name>

*# 자동 동기화 설정*
argocd app set <app-name> --sync-policy automated`

## **보안 고려사항**

## **토큰 관리**

- 최소 권한 원칙 적용
- 정기적인 토큰 갱신
- 토큰 만료일 설정

## **네트워크 보안**

- HTTPS 프로토콜 사용
- 적절한 네트워크 정책 설정
- 인그레스 규칙 검토

## **문제 해결**

## **연결 문제 해결**

`bash*# ArgoCD 서버 로그 확인*
kubectl logs -n argocd deployment/argocd-server

*# 저장소 연결 상태 확인*
argocd repo list`

## **일반적인 문제**

1. 인증 오류
    - 토큰 권한 확인
    - 토큰 만료 여부 확인
2. 동기화 실패
    - 매니페스트 파일 검증
    - 네트워크 연결 확인
