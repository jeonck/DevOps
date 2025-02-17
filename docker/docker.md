# 서버 재기동시 항상 기동 예시
sudo docker run -d --restart always -e "ACCEPT_EULA=Y" -p 8081:80 $NUC_TOOLS docs
