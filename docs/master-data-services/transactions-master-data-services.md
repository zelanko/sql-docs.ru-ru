---
title: Транзакции (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 01/10/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- transactions [Master Data Services], about transactions
- transactions [Master Data Services]
ms.assetid: 4cd2fa6f-9c76-4b7a-ae18-d4e5fd2f03f5
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 09b7d5894f46bca7b493601d9a7df40ed4c0935a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47668082"
---
# <a name="transactions-master-data-services"></a>Транзакции (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]



--------------------------------------------------
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]транзакция регистрируется при каждом выполнении действия с элементом. Все пользователи могут просматривать транзакции, а администраторы также могут их обращать (отменять). Транзакции отображают дату, время и пользователя, выполнившего действие, а также другие сведения. Пользователь может добавить к транзакции заметку, чтобы указать причину выполнения транзакции.  
  
## <a name="when-transaction-are-recorded"></a>Время регистрации транзакций  
 Транзакции записываются, когда элементы:  
  
-   создаются, удаляются или повторно активируются;  
  
-   изменяют значения своих атрибутов;  
  
-   перемещаются по иерархии.  
  
 Когда бизнес-правила изменяют значения атрибутов, транзакции не регистрируются.  
  
## <a name="view-and-manage-transactions"></a>Просмотр и управление транзакциями  
 В функциональной области **Обозреватель** вы можете просматривать сделанные вами транзакции и добавлять к ним заметки (примечания). 
  
 В функциональной области **Управление версиями** администратор может просматривать все транзакции всех пользователей для моделей, к которым у них имеется доступ, а также обращать любые такие транзакции.
 
> [!NOTE]  
>  Администраторы могут просматривать все транзакции всех пользователей до тех пор, если только в функциональной области **Управление версиями** для них не задан уровень разрешений только для чтения. Например, если у администратора есть разрешение только на чтение и разрешение на обновление, он не сможет просматривать транзакции других пользователей, так как разрешение только на чтение имеет приоритет над разрешением на обновление.
  
 Вы можете настроить длительность хранения данных журнала транзакций. Для этого необходимо определить свойство **Срок хранения журнала, дн.** в системных параметрах базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , а также задать значение **Хранение журнала в днях** при создании или изменении модели. Дополнительные сведения см. в разделах [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md) и [Создание модели (службы Master Data Services)](../master-data-services/create-a-model-master-data-services.md).  
  
 MDS_MDM_Sample_Log_Maintenace, задание агента SQL Server, инициирует очистку журналов транзакций и запускается каждую ночь. Для изменения расписания для этого задания можно использовать агент SQL Server.  
  
 Кроме того, для очистки журналов транзакций можно вызвать следующие хранимые процедуры.  
  
|Хранимая процедура|Описание|  
|----------------------|-----------------|  
|mdm.udpTransactionsCleanup|Очищает журнал транзакций|  
|mdm.udpValidationsCleanup|Очищает журнал проверки|  
|mdm.udpEntityStagingBatchTableCleanup|Очищает промежуточную таблицу|  
  
 **Образец**  
  
```  
DECLARE @CleanupOlderThanDate date = '2014-11-11',  
@ModelID INT = 7  
--Clean up Transaction Logs  
EXEC mdm.udpTransactionsCleanup @ModelID, @CleanupOlderThanDate;  
  
--Clean up Validation History  
EXEC mdm.udpValidationsCleanup @ModelID, @CleanupOlderThanDate;  
  
--Clean up EBS tables  
EXEC mdm.udpEntityStagingBatchTableCleanup @ModelID, @CleanupOlderThanDate;  
  
```  
  
## <a name="system-settings"></a>Системные настройки  
 В программе [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] имеется параметр, который определяет, записываются ли транзакции для промежуточных записей. Этот параметр можно настроить в программе [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] или непосредственно в таблице системных параметров в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
 При импорте данных из этой версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] можно указать, следует ли вести журнал транзакций при инициировании хранимых процедур. Дополнительные сведения см. в разделе [Промежуточная хранимая процедура (службы Master Data Services)](../master-data-services/staging-stored-procedure-master-data-services.md).  
  
## <a name="concurrency"></a>Параллелизм  
 Если значение определенной сущности одновременно отображается в нескольких сеансах обозревателя, это значение может изменяться одновременно несколькими пользователями. Службы MDS не обнаруживают одновременные изменения автоматически. Такая ситуация возможна, когда несколько пользователей работают в обозревателе служб MDS в веб-браузере, например в нескольких сеансах, на нескольких вкладках браузера или в нескольких его окнах либо из-под нескольких учетных записей пользователей.  
  
 Несколько пользователей могут обновлять одно значение сущности без ошибок несмотря на то, что транзакции включены. Обычно приоритет получает изменение, которое по времени было внесено последним. Администратор может просмотреть конфликты, возникающие при одновременном внесении нескольких одинаковых изменений, в журнале транзакций и вручную разрешить их. В журнале транзакций отображаются отдельные транзакции для **предыдущего значения** и **нового значения** для рассматриваемого атрибута из каждого сеанса, однако конфликты, возникающие, если для одного старого значения существуют несколько **новых значений** , автоматически не разрешаются.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Отмена действия путем обращения транзакции (только администраторы).|[Отмена транзакции (службы Master Data Services)](../master-data-services/reverse-a-transaction-master-data-services.md)|  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Публикация блога [Transactions, Validation Issue and Staging table cleanup](http://go.microsoft.com/fwlink/p/?LinkId=615374)(Транзакции, проблема проверки и очистка промежуточной таблицы) на портале msdn.com.  
  
## <a name="related-content"></a>См. также  
  
-   [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md)  
  
-   [Заметки (службы Master Data Services)](../master-data-services/annotations-master-data-services.md)  
  
  
