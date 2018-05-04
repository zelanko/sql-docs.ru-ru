---
title: Развертывание кластера Pacemaker для SQL Server для Linux | Документы Microsoft
description: Этот учебник показывает, как для развертывания кластера Pacemaker для SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/11/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.openlocfilehash: 6080c2bb4a430b25bdaa8605b4fd9473cf766fdd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="deploy-a-pacemaker-cluster-for-sql-server-on-linux"></a>Развертывание кластера Pacemaker для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Руководстве документируются задач, необходимых для развертывания кластера Linux Pacemaker для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] всегда группы доступности (AG) или экземпляра отказоустойчивого кластера (FCI). В отличие от тесно связанные Windows Server или[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] стека, Pacemaker создания кластера, а также доступности (AG) группа конфигурации в Linux можно сделать до или после установки [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. После настройки кластера выполняется интеграция и настраивать ресурсы для части Pacemaker развертывания группы Доступности или экземпляр отказоустойчивого Кластера.
> [!IMPORTANT]
> Группы Доступности с типом кластера нет *не* требует Pacemaker кластера, а также осуществляется с помощью Pacemaker. 

> [!div class="checklist"]
> * Установить надстройку высокого уровня доступности и установите Pacemaker.
> * Подготовка узлов к Pacemaker (RHEL и Ubuntu только).
> * Создание кластера Pacemaker.
> * Установите пакеты SQL Server высокой ДОСТУПНОСТИ и агент SQL Server.
 
## <a name="prerequisite"></a>Предварительные требования
[Установка SQL Server 2017 г](sql-server-linux-setup.md).

## <a name="install-the-high-availability-add-on"></a>Установить надстройку высокого уровня доступности
Для установки пакетов, входящие в состав надстройки высокого уровня доступности (HA) для каждого дистрибутив Linux, используйте следующий синтаксис. 

**Red Hat Enterprise Linux (RHEL)**
1.  Зарегистрируйте сервер, используя следующий синтаксис. Запрашивается имя пользователя и пароль.
    
    ```bash
    sudo subscription-manager register
    ```
    
2.  Список доступных пулов для регистрации.
    
    ```bash
    sudo subscription-manager list --available
3.  Run the following command to associate RHEL high availability with the subscription
    
    ```bash
    sudo subscription-manager attach --pool=<PoolID>
    ```
    
    где *PoolId* идентификатор пула для высокого уровня доступности подписки из предыдущего шага.
    
4.  Включите репозитория иметь возможность использования надстройки высокого уровня доступности.
    
    ```bash
    sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
    ```
    
5.  Установите Pacemaker.
    
    ```bash
    sudo yum install pacemaker pcs fence-agents-all resource-agents
    ```

**Ubuntu**

```bash
sudo apt-get install pacemaker pcs fence-agents resource-agents
```

**SUSE Linux Enterprise Server (SLES)**

Установить шаблон высокого уровня доступности в YaST или сделать его как часть установки основного сервера. Установку можно сделать с ISO или DVD-ДИСКОВ, как источник или получение в Интернете.
> [!NOTE]
> На SLES надстройка HA инициализируется при создании кластера.

## <a name="prepare-the-nodes-for-pacemaker-rhel-and-ubuntu-only"></a>Подготовка узлов к Pacemaker (RHEL и Ubuntu только)
Pacemaker сам использует пользователем, созданным на распределение с именем *hacluster*. Пользователь получает создаются при установке надстройки высокой ДОСТУПНОСТИ на RHEL и Ubuntu.
1. На каждом сервере, который будет служить в качестве узла кластера Pacemaker создайте пароль для пользователя, для использования в кластере. Имя, используемое в примерах *hacluster*, но можно использовать любое имя. Имя и пароль должны совпадать на всех узлах, участвующих в кластере Pacemaker.
   
    ```bash
    sudo passwd hacluster
    ```
    
2. На каждом узле, который будет частью кластера Pacemaker, включить и запустить `pcsd` службы с помощью следующих команд (RHEL и Ubuntu):

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   ```
   
   Затем выполните
   
   ```bash
   sudo systemctl status pcsd
   ```
   
   Чтобы убедиться, что `pcsd` запущена.
3. Включите службу Pacemaker на каждый возможный узел кластера Pacemaker.
   
   ```bash
   sudo systemctl start pacemaker
   ```

   В Ubuntu появится сообщение об ошибке:
   
   *по умолчанию-начало pacemaker содержит не runlevels прерывание.*
   
   Эта ошибка может возникнуть проблема. Несмотря на ошибки Включение службы Pacemaker завершилась успешно, и эта ошибка будет исправлена в некоторый момент в будущем.
   
4. Далее создайте и запустите Pacemaker кластер. Отсутствует одно из отличий между RHEL и Ubuntu на данном этапе. Пока на обоих распределения установка `pcs` настраивает файл конфигурации по умолчанию для любой существующей конфигурации уничтожает Pacemaker кластера, на RHEL, при выполнении данной команды и создает новый кластер.

<a id="create"></a>
## <a name="create-the-pacemaker-cluster"></a>Создание кластера Pacemaker 
В этом разделе приведены инструкции по созданию и настройке кластера для каждого распределения Linux.

**RHEL**

1. Разрешить узлы
   
   ```bash
   sudo pcs cluster auth <Node1 Node2 … NodeN> -u hacluster
   ```
   
   где *NodeX* имя узла.
2. Создание кластера
   
   ```bash
   sudo pcs cluster setup --name <PMClusterName Nodelist> --start --all --enable
   ```
   
   где *PMClusterName* — имя, назначенное кластеру Pacemaker и *Nodelist* — список имен узлов, разделенных пробелом.

**Ubuntu**

Настройка Ubuntu аналогично RHEL. Однако есть одно из основных отличий: Установка пакетов Pacemaker создает базовой конфигурации для кластера и включает и запускает `pcsd`. При попытке настроить кластер Pacemaker, следуя инструкциям RHEL точно, возникает сообщение об ошибке. Чтобы устранить эту проблему, выполните следующие действия. 
1. Удалите конфигурацию по умолчанию Pacemaker из каждого узла.
   
   ```bash
   sudo pcs cluster destroy
   ```
   
2. Следуйте указаниям в разделе RHEL для создания кластера Pacemaker.

**SLES**

Процесс создания кластера Pacemaker полностью отличается от на SLES RHEL и Ubuntu. Создание кластера с SLES документов: следующие действия.
1. Начать процесс настройки кластера, запустив 
   ```bash
   sudo ha-cluster-init
   ``` 
   
   на одном из узлов. Может потребоваться NTP не настроен и что устройство наблюдения не обнаружено. Это нормально для Основные приемы и выполнения. При использовании разграничения встроенных SLES который выполняется на основе хранилища STONITH связанного наблюдения. NTP и наблюдения можно настроить позже.
   
2. Вам будет предложено настроить Corosync. Требуется сетевой адрес для привязки, а также адрес многоадресной рассылки и порт. Сетевой адрес задан подсети, в которой вы используете; Например, 192.191.190.0. Можно принять значения по умолчанию в каждой строке, или при необходимости изменить.
   
3. После этого будет предложено, если вы хотите настроить одновременной передачи данных, который является разграничения на диске. Эту конфигурацию можно сделать позже, при необходимости. Если одновременной передачи данных не настроен, в отличие от RHEL и Ubuntu, `stonith-enabled` по умолчанию устанавливается значение false.
   
4. Наконец будет предложено, если вы хотите настроить IP-адрес для администрирования. Этот IP-адрес не обязательно, но функционирует аналогично IP-адрес для отказоустойчивого кластера Windows Server (WSFC) в том смысле, что он создает IP-адрес кластера для использования для подключения к нему через HA Web Konsole (HAWK). Эта конфигурация также является необязательным.
   
5. Убедитесь, что кластер является запущен и работает, выполнив 
   ```bash
   sudo crm status
   ```
   
6. Изменение *hacluster* пароль 
   ```bash
   sudo passwd hacluster
   ```
   
7. Если вы настроили IP-адрес для администрирования, можно проверить его в браузере, который также проверяет изменение пароля для *hacluster*.
   ![](./media/sql-server-linux-deploy-pacemaker-cluster/image2.png)
   
8. На другом сервере SLES, который будет узлом кластера запустите 
   ```bash
   sudo ha-cluster-join
   ```
   
9. При появлении запроса введите имя или IP-адрес сервера, который был настроен в качестве первого узла кластера в предыдущих шагах. Сервер добавляется в качестве узла к существующему кластеру.
   
10. Убедитесь, что узел был добавлен, выполнив 
   ```bash
   sudo crm status
   ```
   
11. Изменение *hacluster* пароль 
   ```bash
   sudo passwd hacluster
   ```
   
12. Повторите шаги с 8 по 11 для всех серверов, добавляемых в кластер.

## <a name="install-the-sql-server-ha-and-sql-server-agent-packages"></a>Установить пакеты SQL Server высокой ДОСТУПНОСТИ и агент SQL Server
Используйте следующие команды для установки SQL Server высокой ДОСТУПНОСТИ пакета и [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] агент, если они уже не установлены. Установка пакета высокой ДОСТУПНОСТИ после установки [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] требует перезагрузки [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] его использовать. Эти инструкции предполагают, что репозиториев для пакетов Microsoft уже были настроены, поскольку [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] должен быть установлен на этом этапе.
> [!NOTE]
> - Если вы не будете использовать [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] агента для доставки журналов или любое другое использование его нужно установить, поэтому пакета *mssql-server-agent* можно пропустить.
> - Дополнительные пакеты для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] в Linux, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Full-Text Search (*mssql-server-fts*) и [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] службы Integration Services (*mssql сервер является*), не являются требуется для обеспечения высокой доступности, либо на экземпляре отказоустойчивого Кластера или группе Доступности.

**RHEL**

```bash
sudo yum install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

**Ubuntu**

```bash
sudo apt-get install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

**SLES**

```bash
sudo zypper install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

## <a name="next-steps"></a>Следующие шаги

В этом учебнике вы узнали, как для развертывания кластера Pacemaker для SQL Server в Linux. Узнать, как для:
> [!div class="checklist"]
> * Установить надстройку высокого уровня доступности и установите Pacemaker.
> * Подготовка узлов к Pacemaker (RHEL и Ubuntu только).
> * Создание кластера Pacemaker.
> * Установите пакеты SQL Server высокой ДОСТУПНОСТИ и агент SQL Server.

Для создания и настройки группы доступности для SQL Server в Linux, см.:

> [!div class="nextstepaction"]
> [Создание и настройка группы доступности для SQL Server в Linux](sql-server-linux-create-availability-group.md).

