---
title: "Настройка параметра конфигурации сервера index create memory | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: index create memory option
ms.assetid: 3d722d9b-bada-4bf5-a9d7-bfc556bb4915
caps.latest.revision: "30"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0c9e2a10cd21015fa56a2081e359baf3b9198064
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="configure-the-index-create-memory-server-configuration-option"></a>Настройка параметра конфигурации сервера index create memory
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются способы настройки параметра конфигурации сервера **index create memory** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **index create memory** управляет максимальным объемом памяти, изначально выделенным для создания индексов. Значение этого параметра по умолчанию равно 0 (настраивается автоматически). Если в дальнейшем для создания индекса потребуется больший объем памяти и такой объем будет доступен, то сервер будет его использовать, тем самым превысив установку этого параметра. Если не будет доступной дополнительной памяти, то создание индекса продолжится с использованием уже выделенной памяти.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка значения параметра index create memory с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Продолжение**  [после настройки параметра index create memory](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Значение параметра **min memory per query** имеет преимущество перед значением параметра **index create memory** . Если изменяются оба параметра и значение параметра **index create memory** меньше значения **min memory per query**, то в системе отобразится предупреждающее сообщение, но это значение будет установлено. При выполнении запроса система выдаст такое же сообщение.  
  
-   При использовании секционированных таблиц и индексов требования к минимальному объему памяти для создания индексов могут быть значительно увеличены при наличии несвязанных секционированных индексов и большой степени параллелизма. Этот параметр управляет общим начальным объемом памяти, выделенным для всех секций индекса в одной операции создания индекса. Если объем, установленный данным параметром меньше, чем минимально необходимый для выполнения запроса, то выполнение запроса прервется с сообщением об ошибке.  
  
-   Рабочее значение этого параметра не будет превышать фактический объем памяти, используемый операционной системой и платформой оборудования, на которой выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Параметр **index create memory** настраивается автоматически, и, как правило, дополнительная настройка не требуется. Однако при возникновении затруднений при создании индексов можно попробовать увеличить значение этого параметра.  
  
###  <a name="Security"></a> Безопасность  
  
####  <a name="Permissions"></a> Разрешения  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-index-create-memory-option"></a>Настройка параметра index create memory  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Память** .  
  
3.  В свойстве **Память для создания индекса**введите или выберите необходимое значение параметра.  
  
     Параметр **index create memory** предназначен для управления объемом памяти, используемой операциями сортировки при создании индексов. Параметр **Память при создании индекса** конфигурируется автоматически, и в большинстве случаев его дополнительная настройка не требуется. Однако при возникновении затруднений при создании индексов можно попробовать увеличить значение этого параметра. Операции сортировки в запросах управляются параметром **min memory per query** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-index-create-memory-option"></a>Настройка параметра index create memory  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `index create memory` равным `4096`.  
  
```tsql  
USE AdventureWorks2012 ;  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
EXEC sp_configure 'index create memory', 4096  
GO  
RECONFIGURE;  
GO  
```  
  
 Дополнительные сведения см. в статье [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Продолжение: после настройки параметра index create memory  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера «Server Memory»](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
