# vmarkitanov_infra
vmarkitanov Infra repository

# ДЗ 6. Деплой тестового приложения
# ------------------------------------------------------------------------------------------------------------
Установлен yc CLI 
Создан хост с помощью yc CLI
На созданном хосте установлен ruby
На созданном хосте установлен mongodb
Загружено и запущено тестовое приложение
Данные для входа:

testapp_IP = 178.154.203.137
testapp_port = 9292

Созданы три скрипта install_ruby.sh, install_mongodb.sh и deploy.sh для  установки необходимых пакетов и разворачивания приложения


# ДЗ 5. Знакомство с облачной инфраструкт фраструктурой. Yandex.Cloud
# ------------------------------------------------------------------------------------------------------------

Для подключения с помощью одной комманды SSH к someinternalhost  я использовал возможность работы через Jamp Proxy:
	ssh -i ~/.ssh/appuser -J appuser@178.154.247.182 appuser@10.128.0.22

Для подключения из консоли при помощи строки вида ssh someinternalhost я настроил алиасы для bastion и someinternalhost. 
Это делается в файле ~/.ssh/config. Ниже привел его содержимое:

Host bastion
    HostName 178.154.247.182
    User appuser
    IdentityFile ~/.ssh/appuser
Host someinternalhost
    Hostname 10.128.0.22
    user appuser
    ProxyJump bastion

Для подключения к станциям bastion и someinternalhost по локальным адресам на станции bastion был установлен VPN сервер pritunl.
В настройках сервера была настроена возможность подключения к панели управления VPN сервера с использованием валидного сертификата. 
Чтобы подключиться к панели с валидным сертификатом необходимо использовать следующую строку подключения :
	https://178.154.247.182.sslip.io
Для подключения VPN клиента используется логин test которому я сменил пин для подключения на более короткий - 140274. Если необходимо могу вернуть на длинный набор цифр

Данные для подключения следующие:
bastion_IP = 178.154.247.182
someinternalhost_IP = 10.128.0.22
