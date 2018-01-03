---
title: "Установка PolyBase | Документация Майкрософт"
ms.custom: 
ms.date: 08/31/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: polybase
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-polybase
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PolyBase, installation
ms.assetid: 3a1e64be-9bfc-4408-accd-35990e1a6b52
caps.latest.revision: "25"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 982594dc9a0f3ec83dcecef9738b2d4cda1fad83
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2018
---
# <a name="polybase-installation"></a>Установка PolyBase
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Чтобы установить пробную версию SQL Server, перейдите на страницу [ознакомительных версий SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016). 
  
## <a name="prerequisites"></a>предварительные требования  
  
-   64-разрядный выпуск ознакомительной версии SQL Server;  
  
-   Microsoft .NET Framework 4.5.  
  
-   Oracle Java SE RunTime Environment (JRE) 7.51 или более поздняя версия (64-разрядный выпуск) (подойдет [JRE](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) или [Server JRE](http://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html) ). Откройте страницу [Загрузка Java SE](http://www.oracle.com/technetwork/java/javase/downloads/index.html). — программа установки столкнется с ошибкой, если JRE будет отсутствовать;  
  
-   минимальный объем памяти: 4 ГБ;  
  
-   минимальное свободное место на жестком диске: 2 ГБ.  
  
-   Для корректной работы Polybase должен быть включен протокол TCP/IP. TCP/IP включен по умолчанию во всех выпусках SQL Server, кроме Developer и Express. Для корректной работы Polybase в выпусках Developer и Express нужно включить подключение по TCP/IP. См. раздел [Enable or Disable a Server Network Protocol](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) (Включение и отключение сетевого протокола сервера).
  
 **Примечания**  
  
 PolyBase можно установить только на одном экземпляре SQL Server на компьютере.  
  
## <a name="single-node-or-polybase-scaleout-group"></a>Один узел или масштабируемая группа PolyBase
Прежде чем начать установку PolyBase на экземплярах SQL Server, вам следует выбрать режим этой установки: на одном узле или в масштабируемой группе PolyBase. Для создания масштабируемой группы PolyBase должны соблюдаться следующие условия. 
- Все компьютеры находятся в одном домене.
- На всех компьютерах используются одинаковые имена и пароли учетной записи службы.
- Экземпляры SQL Server могут взаимодействовать друг с другом по сети.

После установки PolyBase режим установки (автономная или в масштабируемой группе) изменить нельзя. Чтобы перейти от одного режима к другому, следует удалить весь компонент и переустановить его заново.

## <a name="install-using-the-installation-wizard"></a>Установка при помощи мастера установки  
  
1.  Запустите **центр установки SQL Server**. Вставьте установочный носитель SQL Server и дважды щелкните **Setup.exe**.  
  
2.  Щелкните **Установка**, затем **Новая установка автономного SQL Server или добавление компонентов**.  
  
3.  На странице выбора компонентов выберите пункт **Служба запросов PolyBase для внешних данных**.  
  
4.  На странице "Конфигурация сервера" настройте **службу SQL Server PolyBase Engine** и службу перемещения данных SQL Server PolyBase для запуска под одной учетной записью.  
  
    > **ВАЖНО!** В масштабируемой группе PolyBase служба PolyBase Engine и служба перемещения данных PolyBase должны выполняться на всех узлах под одной доменной учетной записью.  
    > См. статью о масштабировании PolyBase.  
  
5.  На **странице настройки PolyBase**выберите один из двух вариантов. Дополнительные сведения см. в статье [Масштабируемые группы PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md) .  
  
    -   Использование экземпляра SQL Server в качестве автономного экземпляра с поддержкой PolyBase  
  
         Выберите этот вариант, чтобы использовать данный экземпляр SQL Server в качестве автономного головного узла.  
  
    -   Использование экземпляра SQL Server в составе масштабируемой группы PolyBase  При выборе этого варианта брандмауэр откроет входящие подключения к SQL Server Database Engine, SQL Server PolyBase Engine, службе перемещения данных SQL Server PolyBase и обозревателю SQL. Брандмауэр будет открыт для входящих подключений от других узлов в масштабируемой группе PolyBase.  
  
         При выборе этого параметра также будут включены в брандмауэре подключения для координатора распределенных транзакций (MSDTC) и изменены параметры реестра для MSDTC.  
  
6.  На **странице настройки PolyBase**укажите диапазон портов, включающий не менее шести портов. Программа установки SQL Server выделит первые шесть доступных портов из указанного диапазона.  
  
##  <a name="installing"></a> Установка с помощью командной строки  
 Используйте значения из этой таблицы для создания сценариев установки. Две службы ( **SQL ServerPolyBase Engine** и **служба перемещения данных SQL Server PolyBase** ) должны запускаться под одной и той же учетной записью. В масштабируемой группе PolyBase обе службы PolyBase должны выполняться на всех узлах под одной доменной учетной записью.  
  
|Компонент SQL Server|Параметр и значения|Description|  
|--------------------------|--------------------------|-----------------|  
|Управление программой установки SQL Server|**Обязательное**<br /><br /> /FEATURES=PolyBase|Выбирает компонент PolyBase.|  
|Компонент SQL Server PolyBase Engine|**Необязательно**<br /><br /> /PBENGSVCACCOUNT|Задает учетную запись для службы ядра. По умолчанию используется **NT Authority\NETWORK SERVICE**.|  
|Компонент SQL Server PolyBase Engine|**Необязательно**<br /><br /> /PBENGSVCPASSWORD|Задает пароль для учетной записи службы ядра.|  
|Компонент SQL Server PolyBase Engine|**Необязательно**<br /><br /> /PBENGSVCSTARTUPTYPE|Задает режим запуска для службы PolyBase Engine: Automatic (автоматически, используется по умолчанию), Disabled (отключена) или Manual (вручную).|  
|Служба перемещения данных SQL Server PolyBase|**Необязательно**<br /><br /> /PBDMSSVCACCOUNT|Задает учетную запись для службы перемещения данных. По умолчанию используется **NT Authority\NETWORK SERVICE**.|  
|Служба перемещения данных SQL Server PolyBase|**Необязательно**<br /><br /> /PBDMSSVCPASSWORD|Задает пароль для учетной записи службы перемещения данных.|  
|Служба перемещения данных SQL Server PolyBase|**Необязательно**<br /><br /> /PBDMSSVCSTARTUPTYPE|Задает режим запуска для службы перемещения данных: Automatic (автоматически, используется по умолчанию), Disabled (отключена) или Manual (вручную).|  
|PolyBase|**Необязательно**<br /><br /> /PBSCALEOUT|Указывает, будет ли этот экземпляр SQL Server использоваться в составе вычислительной масштабируемой группы PolyBase. <br />Поддерживаемые значения: **True**, **False**|  
|PolyBase|**Необязательно**<br /><br /> /PBPORTRANGE|Указывает диапазон портов для служб PolyBase, включающий не менее 6 портов. Пример<br /><br /> `/PBPORTRANGE=16450-16460`|  
  
 **Пример**  
  
 Далее представлен пример сценария установки.  
  
```  
  
Setup.exe /Q /ACTION=INSTALL /IACCEPTSQLSERVERLICENSETERMS /FEATURES=SQLEngine,Polybase   
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="\<fabric-domain>\Administrator"   
/INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /PBSCALEOUT=TRUE   
/PBPORTRANGE=16450-16460 /SECURITYMODE=SQL /SAPWD="<StrongPassword>"   
/PBENGSVCACCOUNT="<DomainName>\<UserName>" /PBENGSVCPASSWORD="<StrongPassword>"   
/PBDMSSVCACCOUNT="<DomainName>\<UserName>" /PBDMSSVCPASSWORD="<StrongPassword>"  
  
```  
  
## <a name="post-installation-notes"></a>Действия после установки  
 PolyBase устанавливает три пользовательские базы данных: DWConfiguration, DWDiagnostics и DWQueue.   Они предназначены для PolyBase, поэтому изменять или удалять их не следует.  
  
### <a name="how-to-confirm-installation"></a>Подтверждение установки  
 Выполните следующую команду. Если служба PolyBase установлена, она возвращает значение 1, а если нет — значение 0.  
  
```sql  
SELECT SERVERPROPERTY ('IsPolybaseInstalled') AS IsPolybaseInstalled;  
```  
  
### <a name="firewall-rules"></a>Правила брандмауэра  
 Программа установки SQL Server PolyBase создает на компьютере следующие правила брандмауэра:  
  
-   SQL Server PolyBase — ядро СУБД — \<имя_экземпляра_SQL_Server> (входящие TCP-соединения);  
  
-   SQL Server PolyBase — службы PolyBase — \<имя_экземпляра_SQL_Server> (входящие TCP-соединения);  
  
-   SQL Server PolyBase — обозреватель SQL — (UDP вход.).  
  
 Если во время установки вы выбрали использование экземпляра SQL Server в составе масштабируемой группы PolyBase, эти правила будут включены и брандмауэр будет открыт для входящих подключений к SQL Server Database Engine, SQL Server PolyBase Engine, к службе перемещения данных SQL Server PolyBase и обозревателю SQL. Но если во время установки служба брандмауэра не запущена на компьютере, программа установки SQL Server не сможет включить эти правила. В этом случае необходимо запустить службу брандмауэра и включить эти правила после установки.  
  
#### <a name="to-enable-the-firewall-rules"></a>Включение правил брандмауэра  
  
-   Откройте **Панель управления**.  
  
-   Щелкните **Система и безопасность**, а затем — **Брандмауэр Windows**.  
  
-   Щелкните **Дополнительные параметры**, затем нажмите элемент **Правила для входящих подключений**.  
  
-   Щелкните отключенное правило правой кнопкой мыши и выберите пункт меню **Включить правило**.  
  
### <a name="polybase-service-accounts"></a>Учетные записи служб PolyBase
Чтобы изменить учетные записи служб для PolyBase Engine и служб перемещения данных PolyBase, удалите и снова установите компонент PolyBase.
   
## <a name="next-steps"></a>Следующие шаги  
 См. раздел [PolyBase configuration](../../relational-databases/polybase/polybase-configuration.md).  
  
  
