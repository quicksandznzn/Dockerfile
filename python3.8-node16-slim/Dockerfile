FROM python:3.8-slim
COPY . /workspace
WORKDIR /workspace
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak \
    && echo "deb http://mirrors.ustc.edu.cn/debian/ buster main" >>/etc/apt/sources.list \
    && echo "deb-src http://mirrors.ustc.edu.cn/debian/ buster main" >>/etc/apt/sources.list \
    && echo "deb http://mirrors.ustc.edu.cn/debian-security buster/updates main" >>/etc/apt/sources.list \
    && echo "deb-src http://mirrors.ustc.edu.cn/debian-security buster/updates maein" >>/etc/apt/sources.list \
    && echo "deb http://mirrors.ustc.edu.cn/debian/ buster-updates main" >>/etc/apt/sources.list \
    && echo "deb-src http://mirrors.ustc.edu.cn/debian/ buster-updates main" >>/etc/apt/sources.list

RUN apt-get update
RUN apt-get install xz-utils
RUN apt-get install -y curl
RUN apt-get install -y wget

RUN wget https://nodejs.org/dist/v16.13.1/node-v16.13.1-linux-x64.tar.xz
# Extract & install
RUN tar -xf node-v16.13.1-linux-x64.tar.xz -C /opt/
RUN ln -s /opt/node-v16.13.1-linux-x64/bin/node /usr/local/bin/node
RUN ln -s /opt/node-v16.13.1-linux-x64/bin/npm /usr/local/bin/npm
RUN ln -s /opt/node-v16.13.1-linux-x64/bin/npx /usr/local/bin/npx

RUN npm install jsdom --registry https://registry.npm.taobao.org
RUN pip install --upgrade pip -i https://pypi.tuna.tsinghua.edu.cn/simple
RUN pip  --default-timeout=1000 install  -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple