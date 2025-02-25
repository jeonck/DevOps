# 서버 재기동시 항상 기동 예시
sudo docker run -d --restart always -e "ACCEPT_EULA=Y" -p 8081:80 $NUC_TOOLS docs


# 이미지 제거 후 재 빌드 시 
# 기존 이미지 제거
docker rmi temperature-aggregator:1.0
docker rmi sample.azurecr.io/temperature-aggregator:1.0

# 올바른 플랫폼으로 다시 빌드
docker build --platform linux/amd64 -t temperature-aggregator:1.0 .

# 태그 지정 및 푸시
docker tag temperature-aggregator:1.0 sample.azurecr.io/temperature-aggregator:1.0
docker push sample.azurecr.io/temperature-aggregator:1.0

