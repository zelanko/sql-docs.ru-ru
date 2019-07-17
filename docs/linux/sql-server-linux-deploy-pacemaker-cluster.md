---
title: Развертывание кластера Pacemaker для SQL Server в Linux
description: Этом руководстве показано, как развернуть кластер Pacemaker для SQL Server в Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 12/11/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: ee3b4aac2e1bcdcc37de17a569f080d3b9bc87cc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077480"
---
# <a name="deploy-a-pacemaker-cluster-for-sql-server-on-linux"></a>Развертывание кластера Pacemaker для SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Этот учебник описывает задачи, необходимые для развертывания кластера Pacemaker в Linux для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] группы доступности AlwaysOn (группы Доступности) или экземпляра отказоустойчивого кластера (FCI). В отличие от тесно связанные Windows Server / [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] стека, создание кластера Pacemaker, а также конфигурации (AG) группы доступности в Linux может выполняться до или после установки [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. После настройки кластера выполняется интеграция, так и настройку ресурсов для части Pacemaker развертывания группы Доступности или экземпляра отказоустойчивого Кластера.
> [!IMPORTANT]
> Группа Доступности с типом кластера нет *не* требует кластера Pacemaker, а также осуществляется с помощью Pacemaker. 

> [!div class="checklist"]
> * Установить надстройку высокий уровень доступности и установке Pacemaker.
> * Подготовка узлов для Pacemaker (RHEL и только Ubuntu).
> * Создание кластера Pacemaker.
> * Установите пакеты высокой ДОСТУПНОСТИ SQL Server и агент SQL Server.
 
## <a name="prerequisite"></a>Предварительные требования
[Установка SQL Server 2017](sql-server-linux-setup.md).

## <a name="install-the-high-availability-add-on"></a>Установить надстройку высокого уровня доступности
Чтобы установить пакеты, составляющие надстройки высокого уровня доступности (HA) для каждого дистрибутив Linux, используйте следующий синтаксис. 

**Red Hat Enterprise Linux (RHEL)**
1.  Зарегистрируйте сервер, используя следующий синтаксис. Будут запрошены имя пользователя и пароль.
    
    ```bash
    sudo subscription-manager register
    ```
    
2.  Получение списка доступных пулов для регистрации.
    
    ```bash
    sudo subscription-manager list --available
    ```

3.  Выполните следующую команду, чтобы связать RHEL высокого уровня доступности с подпиской
    
    ```bash
    sudo subscription-manager attach --pool=<PoolID>
    ```
    
    где *PoolId* идентификатор пула для высокого уровня доступности подписки из предыдущего шага.
    
4.  Включите репозиторий иметь возможность использования надстройки высокого уровня доступности.
    
    ```bash
    sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
    ```
    
5.  Установка Pacemaker.
    
    ```bash
    sudo yum install pacemaker pcs fence-agents-all resource-agents
    ```

**Ubuntu**

```bash
sudo apt-get install pacemaker pcs fence-agents resource-agents
```

**SUSE Linux Enterprise Server (SLES)**

Установите шаблон высокого уровня доступности в YaST или сделать его как часть установки основного сервера. Установка может выполняться с помощью ISO DVD, как источник или, получив его через Интернет.
> [!NOTE]
> В SLES дополнение HA инициализируется при создании кластера.

## <a name="prepare-the-nodes-for-pacemaker-rhel-and-ubuntu-only"></a>Подготовка узлов для Pacemaker (RHEL и только Ubuntu)
Pacemaker использует пользователем, созданным на распределение с именем *hacluster*. Пользователь создается при установке надстройки высокого уровня ДОСТУПНОСТИ на RHEL и Ubuntu.
1. На каждом сервере, который будет использоваться в качестве узла кластера Pacemaker создайте пароль для пользователя, используемый кластером. — Имя, используемое в примерах *hacluster*, но можно использовать любое имя. Имя и пароль должны совпадать на всех узлах, участвующих в кластере Pacemaker.
   
    ```bash
    sudo passwd hacluster
    ```
    
2. На каждом узле, который будет частью кластера Pacemaker, включите и запустите `pcsd` службу, выполнив следующие команды (RHEL и Ubuntu):

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   ```
   
   Затем выполните
   
   ```bash
   sudo systemctl status pcsd
   ```
   
   Чтобы убедиться, что `pcsd` запускается.
3. Включите службу Pacemaker на каждой из возможных узлов кластера Pacemaker.
   
   ```bash
   sudo systemctl start pacemaker
   ```

   В Ubuntu появится сообщение об ошибке:
   
   *pacemaker по умолчанию-начало содержит не runlevels, прерывание.*
   
   Эта ошибка является известной проблемой. Несмотря на ошибки Включение службы Pacemaker прошла успешно, и эта ошибка будет исправлена в некоторый момент в будущем.
   
4. Затем создайте и запустите кластер Pacemaker. Есть одно различие между RHEL и Ubuntu на этом этапе. Хотя на обоих дистрибутивов, установка `pcs` автоматически настраивает файл конфигурации по умолчанию в кластере Pacemaker на RHEL, выполнив следующую команду уничтожает все существующие конфигурации и создает новый кластер.

<a id="create"></a>
## <a name="create-the-pacemaker-cluster"></a>Создание кластера Pacemaker 
В этом разделе приведены инструкции для создания и настройки кластера для каждого дистрибутива Linux.

**RHEL**

1. Авторизовать узлы
   
   ```bash
   sudo pcs cluster auth <Node1 Node2 ... NodeN> -u hacluster
   ```
   
   где *NodeX* имя узла.
2. Создание кластера
   
   ```bash
   sudo pcs cluster setup --name <PMClusterName Nodelist> --start --all --enable
   ```
   
   где *PMClusterName* — это имя, назначенное кластеру Pacemaker и *Nodelist* представляет список имен узлов, разделенных пробелом.

**Ubuntu**

Настройка Ubuntu похоже на RHEL. Однако есть одно из основных отличий: при установке пакетов Pacemaker создается базовой конфигурации для кластера и включает и запускает `pcsd`. При попытке настройки кластера Pacemaker в соответствии с инструкциями RHEL точно, вы получите ошибку. Чтобы устранить эту проблему, выполните следующие действия. 
1. Удалите конфигурацию Pacemaker по умолчанию из каждого узла.
   
   ```bash
   sudo pcs cluster destroy
   ```
   
2. Выполните действия, описанные в разделе RHEL для создания кластера Pacemaker.

**SLES**

Процесс создания кластера Pacemaker на SLES совершенно другой, а не на RHEL и Ubuntu. Ниже рассказывается, как создать кластер с SLES.
1. Запустите процесс настройки кластера, выполнив 
   ```bash
   sudo ha-cluster-init
   ``` 
   
   на одном из узлов. Вам может быть предложено NTP не настроен, и, устройства наблюдения не найдено. Это нормально для действия и запуск. Устройство наблюдения связана с STONITH при использовании ограждения встроенные в SLES, на основе хранилища. NTP и устройства наблюдения можно настроить позже.
   
2. Вам будет предложено настроить Corosync. Будет предложено ввести сетевой адрес для привязки, а также порт и адрес многоадресной рассылки. Сетевой адрес — имя подсети, которую вы используете; Например, 192.191.190.0. Можно принять значения по умолчанию в каждой строке, или при необходимости изменить.
   
3. Далее будет предложено, если вы хотите настроить SBD, который является ограждения на диске. Эта конфигурация будет сделано позже при необходимости. Если SBD не настроен, в отличие от RHEL и Ubuntu, `stonith-enabled` по умолчанию устанавливается в значение false.
   
4. Наконец будет предложено, если вы хотите настроить IP-адрес для администрирования. Этот IP-адрес является необязательным, но работает так же, если IP-адрес для отказоустойчивого кластера Windows Server (WSFC) в том смысле, что он создает IP-адрес кластера, используемый для подключения к нему через высокого уровня ДОСТУПНОСТИ Web Konsole (HAWK). Кроме того, эта конфигурация является необязательным.
   
5. Убедитесь, что кластер работает приступить к работе, выполнив 
   ```bash
   sudo crm status
   ```
   
6. Изменение *hacluster* пароль с помощью 
   ```bash
   sudo passwd hacluster
   ```
   
7. Если вы настроили IP-адресом для администрирования, можно проверить его в браузере, который также проверяет изменение пароля для *hacluster*.
   ![](./media/sql-server-linux-deploy-pacemaker-cluster/image2.png)
   
8. На другом сервере SLES, который будет узлом кластера запустите 
   ```bash
   sudo ha-cluster-join
   ```
   
9. При запросе введите имя или IP-адрес сервера, который был настроен в качестве первого узла кластера на предыдущих шагах. Сервер добавляется в качестве узла к существующему кластеру.
   
10. Убедитесь, что узел добавлен, выполнив 
   ```bash
   sudo crm status
   ```
   
11. Изменение *hacluster* пароль с помощью 
   ```bash
   sudo passwd hacluster
   ```
   
12. Повторите шаги 8 – 11, для всех серверов, добавляемых в кластер.

## <a name="install-the-sql-server-ha-and-sql-server-agent-packages"></a>Установите пакеты высокой ДОСТУПНОСТИ SQL Server и агент SQL Server
Используйте следующие команды для установки пакета высокой ДОСТУПНОСТИ SQL Server и [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] агента, если они еще не установлены. Установка пакета высокой ДОСТУПНОСТИ после установки [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] требует перезапуска [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] для его можно использовать. Эти инструкции предполагают, что в репозитории для пакетов Microsoft уже были настроены, поскольку [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] должен быть установлен на этом этапе.
> [!NOTE]
> - Если вы не будете использовать [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] агент для доставки журналов или любого другого использования, его не требуется установить, так что пакета *mssql-server-agent* можно пропустить.
> - Дополнительные пакеты для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] в Linux, [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Full-Text Search (*mssql-server-fts*) и [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] служб Integration Services (*mssql-server находится*), не являются требуется для обеспечения высокой доступности, для экземпляра отказоустойчивого Кластера или группе Доступности.

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

В этом руководстве вы узнали, как развернуть кластер Pacemaker для SQL Server в Linux. Вы узнали, как для:
> [!div class="checklist"]
> * Установить надстройку высокий уровень доступности и установке Pacemaker.
> * Подготовка узлов для Pacemaker (RHEL и только Ubuntu).
> * Создание кластера Pacemaker.
> * Установите пакеты высокой ДОСТУПНОСТИ SQL Server и агент SQL Server.

Чтобы создать и настроить группу доступности для SQL Server в Linux, см. в разделе:

> [!div class="nextstepaction"]
> [Создание и настройка группы доступности для SQL Server в Linux](sql-server-linux-create-availability-group.md).

