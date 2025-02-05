## ArgoCD와 GitLab 연동 가이드

## **소개**

ArgoCD를 GitLab과 연결하여 GitOps 기반의 CI/CD 환경을 구축하는 방법을 설명합니다.

## **연결 절차**

## **1. GitLab 개인 접근 토큰 생성**

1. GitLab에 로그인 후 사용자 설정으로 이동
2. "Access Tokens" 메뉴 선택
3. 새로운 토큰 생성:
    - 토큰 이름 설정
    - 필요한 권한 선택 (read_repository, read_api)
    - 만료 기간 설정
4. 생성된 토큰 안전하게 보관

## **2. Kubernetes 클러스터 준비**

- AWS EKS, GKE, AKS 등 다양한 환경에서 운영 가능
- 클러스터 접근 권한 확인

## **3. ArgoCD 설치**  

*# ArgoCD 네임스페이스 생성*  
`kubectl create namespace argocd`

*# ArgoCD 설치*   
`kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/ha/install.yaml`  

## **4. ArgoCD API 서버 접근 설정**

*# 포트 포워딩 설정*  
`kubectl port-forward svc/argocd-server -n argocd 8080:443`  

## **5. 초기 비밀번호 확인 및 변경**

*# 초기 비밀번호 확인*  
`kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d `  

*# ArgoCD 로그인 및 비밀번호 변경*  
`argocd login ipaddr:80 --insecure`
`argocd account update-password`

## **6. ArgoCD에 GitLab 저장소 추가**

*# CLI 사용*  
`argocd repo add <GITLAB_REPO_URL> --username <USERNAME> --password <PERSONAL_ACCESS_TOKEN>`

## **7. ArgoCD에 cluster 추가**
`argocd cluster add <클러스터 arn 명 : api server address>`

## **8. 애플리케이션 생성**

`argocd app create <app-name> \
  --repo <GITLAB_REPO_URL> \
  --path <PATH_TO_MANIFEST> \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace <NAMESPACE>`

## **유의사항**

## **보안 관련**

- 토큰 권한은 최소한으로 설정
- HTTPS 프로토콜 사용 권장
- 토큰 정기적 갱신

## **연결 테스트**

1. ArgoCD UI에서 연결 상태 확인
2. 저장소 접근 권한 검증
3. ArgoCD 서버 로그 확인

## **CI/CD 파이프라인**

- GitLab CI/CD 파이프라인과 통합 가능
- 코드 변경 시 자동 배포 설정
- 웹훅을 통한 이벤트 처리

## **문제해결**

## **일반적인 문제**

1. 인증 오류
    - 토큰 권한 확인
    - 만료 여부 확인
2. 동기화 실패
    - 매니페스트 검증
    - 네트워크 연결 확인

## **로그 확인**

`kubectl logs -n argocd deployment/argocd-server`

## **참고 문서**

- [ArgoCD 공식 문서](https://argo-cd.readthedocs.io/)
- [GitLab 문서](https://docs.gitlab.com/)
- [Kubernetes 문서](https://kubernetes.io/docs/)


