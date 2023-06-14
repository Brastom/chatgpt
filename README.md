apt install docker.io -y

docker pull techxiaofei/bot-on-anything:latest

docker tag techxiaofei/bot-on-anything bot-on-anything

# 下载配置文件（公众号版），只需要改 api_key 即可
# token可改可不改只要保证和公众号里一样就行

wget -O config.json https://raw.githubusercontent.com/Brastom/chatgpt/main/config.json
# 运行
docker run --name bot-on-anything -d -p 0.0.0.0:80:80 -v "$(pwd)/config.json:/app/config.json" bot-on-anything python app.py

docker logs -f bot-on-anything
