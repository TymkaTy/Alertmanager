# Alertmanager

Общие правила: 
1. Для копипаста использовать ctrl+shift+V
2. Всегда вводить пароль, когда это требуется
3. 

//Устанавливаем wget:

sudo yum install wget

//Скачиваем файл репозитория:
sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo
//Везде прописываем "Y"

//Устанавливаем docker:
sudo yum install docker-ce docker-ce-cli containerd.io

//Запускаем его и разрешаем автозапуск:
sudo systemctl enable docker --now

//Для этого сначала убедимся в наличие пакета curl.
б) На системы RPM:

sudo yum install curl

COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)

//Tеперь скачиваем скрипт docker-compose и помещаем его в каталог /usr/bin:

sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose

//Даем права файлу на исполнение:

sudo chmod +x /usr/bin/docker-compose

//Запускаем docker-compose с выводом его версии:

docker-compose --version

Если на нашем сервере работает брандмауэр, необходимо открыть некторые порты:

9090/tcp — веб-интерфейс для работы с Prometheus.

3000/tcp — графана.

firewall-cmd --permanent --add-port={3000,9090}/tcp

firewall-cmd –reload

Подразумевается, что у нас установлен Docker и docker-compose

Создаем каталоги, где будем создавать наши файлы:

sudo mkdir -p /opt/prometheus_stack/{prometheus,grafana,alertmanager,blackbox}

sudo touch /opt/prometheus_stack/docker-compose.yml

cd /opt/prometheus_stack

Открываем файл: 

sudo vi docker-compose.yml

Создаем конфигурационный файл для prometheus:

sudo vi prometheus/prometheus.yml

После все введённых данных прописывая 

sudo docker compose up -d 

Добавим к нашему стеку графану.

Открываем файл:

sudo vi docker-compose.yml




