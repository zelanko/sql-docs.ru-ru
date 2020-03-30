---
title: Развертывание кластера Pacemaker для SQL Server на Linux
description: В этом руководстве описывается, как развернуть кластер Pacemaker для SQL Server на Linux.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 12/11/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: ee3b4aac2e1bcdcc37de17a569f080d3b9bc87cc
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68077480"
---
# <a name="deploy-a-pacemaker-cluster-for-sql-server-on-linux"></a>Развертывание кластера Pacemaker для SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом руководстве описываются задачи, необходимые для развертывания кластера Pacemaker Linux для группы доступности Always On [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] или экземпляра отказоустойчивого кластера. В отличие от тесно связанного стека Windows Server и [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], создавать кластер Pacemaker, а также настраивать группу доступности в Linux можно как до, так и после установки [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Интеграция и настройка ресурсов для той части группы доступности или экземпляра отказоустойчивого кластера, которая связана с Pacemaker, выполняется после настройки кластера.
> [!IMPORTANT]
> Группа доступности с типом кластера "Нет" *не* требует наличия кластера Pacemaker и не может управляться с помощью Pacemaker. 

> [!div class="checklist"]
> * установка надстройки высокого уровня доступности и Pacemaker;
> * подготовка узлов для Pacemaker (только в RHEL и Ubuntu);
> * создание кластера Pacemaker;
> * Установка пакетов высокого уровня доступности и агента SQL Server
 
## <a name="prerequisite"></a>Предварительные требования
[Установите SQL Server 2017](sql-server-linux-setup.md).

## <a name="install-the-high-availability-add-on"></a>Установите надстройку высокого уровня доступности.
Используйте приведенный ниже синтаксис, чтобы установить пакеты, составляющие надстройку высокого уровня доступности, для каждого дистрибутива Linux. 

**Red Hat Enterprise Linux (RHEL)**
1.  Зарегистрируйте сервер, используя приведенный ниже синтаксис. Вам будет предложено ввести допустимое имя пользователя и пароль.
    
    ```bash
    sudo subscription-manager register
    ```
    
2.  Перечислите доступные пулы для регистрации.
    
    ```bash
    sudo subscription-manager list --available
    ```

3.  Выполните следующую команду, чтобы связать высокий уровень доступности RHEL с подпиской:
    
    ```bash
    sudo subscription-manager attach --pool=<PoolID>
    ```
    
    Здесь *PoolId* — это идентификатор пула для подписки высокого уровня доступности из предыдущего шага.
    
4.  Включите для репозитория возможность использовать надстройку высокого уровня доступности.
    
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

Установите шаблон высокого уровня доступности в YaST или сделайте это в рамках основной установки сервера. Установку можно выполнить из ISO, с DVD-диска либо из сети.
> [!NOTE]
> В SLES надстройка высокого уровня доступности инициализируется при создании кластера.

## <a name="prepare-the-nodes-for-pacemaker-rhel-and-ubuntu-only"></a>Подготовка узлов для Pacemaker (только в RHEL и Ubuntu)
Для Pacemaker используется пользователь *hacluster*, созданный в дистрибутиве. Он создается при установке надстройки высокого уровня доступности в RHEL и Ubuntu.
1. На каждом сервере, который будет служить узлом кластера Pacemaker, создайте пароль для пользователя, используемого кластером. В примерах используется имя *hacluster*, но можно выбрать любое имя. Имя и пароль должны быть одинаковыми во всех узлах, участвующих в кластере Pacemaker.
   
    ```bash
    sudo passwd hacluster
    ```
    
2. В каждом узле, который будет входить в кластер Pacemaker, включите и запустите службу `pcsd` с помощью следующих команд (в RHEL и Ubuntu):

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   ```
   
   Затем выполните следующую команду:
   
   ```bash
   sudo systemctl status pcsd
   ```
   
   чтобы убедиться в том, что средство `pcsd` запущено.
3. Включите службу Pacemaker в каждом возможном узле кластера Pacemaker.
   
   ```bash
   sudo systemctl start pacemaker
   ```

   В Ubuntu произойдет следующая ошибка:
   
   *pacemaker Default-Start contains no runlevels, aborting* (pacemaker Default-Start не содержит уровни выполнения, прерывание).
   
   Это известная проблема. Несмотря на ошибку, служба Pacemaker включается успешно. Эта ошибка будет исправлена в будущем.
   
4. Далее создайте и запустите кластер Pacemaker. На этом этапе между RHEL и Ubuntu есть одно различие. В обоих дистрибутивах при установке `pcs` настраивается файл конфигурации по умолчанию для кластера Pacemaker, однако в RHEL при выполнении этой команды существующая конфигурация удаляется и создается новый кластер.

<a id="create"></a>
## <a name="create-the-pacemaker-cluster"></a>Создание кластера Pacemaker 
В этом разделе описывается, как создать и настроить кластер для каждого дистрибутива Linux.

**RHEL**

1. Авторизуйте узлы.
   
   ```bash
   sudo pcs cluster auth <Node1 Node2 ... NodeN> -u hacluster
   ```
   
   Здесь *NodeX* — это имя узла.
2. Создайте кластер.
   
   ```bash
   sudo pcs cluster setup --name <PMClusterName Nodelist> --start --all --enable
   ```
   
   Здесь *PMClusterName* — это имя, присвоенное кластеру Pacemaker, а *Nodelist* — список имен узлов, разделенных пробелами.

**Ubuntu**

Ubuntu настраивается так же, как RHEL. Однако есть одно важное отличие: при установке пакетов Pacemaker создается базовая конфигурация кластера, а также включается и запускается `pcsd`. Если вы попытаетесь настроить кластер Pacemaker, выполнив точно те же инструкции, что и для RHEL, произойдет ошибка. Чтобы решить эту проблему, выполните указанные ниже действия. 
1. Удалите конфигурацию Pacemaker по умолчанию из каждого узла.
   
   ```bash
   sudo pcs cluster destroy
   ```
   
2. Выполните инструкции по созданию кластера Pacemaker для RHEL.

**SLES**

Процесс создания кластера Pacemaker в SLES совершенно отличается от аналогичного процесса в RHEL и Ubuntu. Ниже описано, как создать кластер для SLES.
1. Начните процесс настройки кластера, выполнив команду 
   ```bash
   sudo ha-cluster-init
   ``` 
   
   в одном из узлов. Может появиться предупреждение о том, что протокол NTP не настроен и устройство наблюдения не найдено. Это не помешает настройке. Устройство наблюдения связано с STONITH, если используется встроенное ограждение SLES на основе хранилища. NTP и устройство наблюдения можно настроить позже.
   
2. Вам предлагается настроить Corosync. Необходимо указать сетевой адрес для привязки, а также адрес и порт многоадресной рассылки. Сетевой адрес — это используемая подсеть, например 192.191.190.0. Во всех запросах можно принять значения по умолчанию или при необходимости изменить их.
   
3. Затем вам будет предложено настроить SBD, то есть ограждение на основе диска. Это при необходимости можно сделать позже. В отличие от RHEL и Ubuntu, если ограждение SBD не настроено, параметр `stonith-enabled` по умолчанию устанавливается в значение false.
   
4. Наконец, вам предлагается настроить IP-адрес для администрирования. Этот IP-адрес является необязательным, но имеет то же значение, что и IP-адрес отказоустойчивого кластера Windows Server (WSFC), то есть создает в кластере IP-адрес для подключения через веб-консоль высокого уровня доступности (HAWK). Эта настройка также является необязательной.
   
5. Убедитесь в том, что кластер настроен и запущен, выполнив следующую команду: 
   ```bash
   sudo crm status
   ```
   
6. Измените пароль пользователя *hacluster* с помощью следующей команды: 
   ```bash
   sudo passwd hacluster
   ```
   
7. Если вы настроили IP-адрес для администрирования, то можете протестировать его в браузере. При этом также проверяется изменение пароля для пользователя *hacluster*.
   ![](./media/sql-server-linux-deploy-pacemaker-cluster/image2.png)
   
8. На другом сервере SLES, который будет узлом кластера, выполните следующую команду: 
   ```bash
   sudo ha-cluster-join
   ```
   
9. При появлении запроса введите имя или IP-адрес сервера, который был настроен в качестве первого узла кластера в предыдущих шагах. Сервер добавляется в качестве узла в существующий кластер.
   
10. Убедитесь в том, что узел был добавлен, с помощью следующей команды: 
   ```bash
   sudo crm status
   ```
   
11. Измените пароль пользователя *hacluster* с помощью следующей команды: 
   ```bash
   sudo passwd hacluster
   ```
   
12. Повторите шаги 8–11 для всех остальных серверов, которые необходимо добавить в кластер.

## <a name="install-the-sql-server-ha-and-sql-server-agent-packages"></a>Установка пакетов высокого уровня доступности и агента SQL Server
Используйте приведенные ниже команды, чтобы установить пакет высокого уровня доступности SQL Server и агент [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], если они еще не установлены. Если пакет высокого уровня доступности был установлен после [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], необходимо перезапустить [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], чтобы этот пакет использовался. В этих инструкциях предполагается, что репозитории для пакетов Майкрософт уже настроены, так как [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] на этом этапе должен быть установлен.
> [!NOTE]
> - Если вы не будете использовать агент [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] для доставки журналов или в других целях, устанавливать его не обязательно, поэтому пакет *mssql-server-agent* можно пропустить.
> - Другие необязательные пакеты для [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] в Linux — пакет полнотекстового поиска ([!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]mssql-server-fts *)*  и пакет [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Integration Services (*mssql-server-is*) — не требуются для обеспечения высокой доступности и экземпляра FCI, и группы доступности.

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

## <a name="next-steps"></a>Дальнейшие действия

В этом руководстве вы узнали, как развернуть кластер Pacemaker для SQL Server на Linux. Вы ознакомились с выполнением следующих задач:
> [!div class="checklist"]
> * установка надстройки высокого уровня доступности и Pacemaker;
> * подготовка узлов для Pacemaker (только в RHEL и Ubuntu);
> * создание кластера Pacemaker;
> * Установка пакетов высокого уровня доступности и агента SQL Server

Чтобы создать и настроить группу доступности для SQL Server на Linux, обратитесь к следующему руководству:

> [!div class="nextstepaction"]
> [Создание и настройка группы доступности для SQL Server на Linux](sql-server-linux-create-availability-group.md)

