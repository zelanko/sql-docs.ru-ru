---
title: Настройка параметра конфигурации сервера index create memory | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- index create memory option
ms.assetid: 3d722d9b-bada-4bf5-a9d7-bfc556bb4915
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 280d4edef062429304d5c6e1d6c65ea63fac2eee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62786966"
---
# <a name="configure-the-index-create-memory-server-configuration-option"></a>Настройка параметра конфигурации сервера index create memory
  В этом разделе описываются способы настройки параметра конфигурации сервера **index create memory** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **index create memory** управляет максимальным объемом памяти, изначально выделенным для создания индексов. Значение этого параметра по умолчанию равно 0 (настраивается автоматически). Если в дальнейшем для создания индекса потребуется больший объем памяти и такой объем будет доступен, то сервер будет его использовать, тем самым превысив установку этого параметра. Если не будет доступной дополнительной памяти, то создание индекса продолжится с использованием уже выделенной памяти.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка значения параметра index create memory с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра index create memory](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Значение параметра **min memory per query** имеет преимущество перед значением параметра **index create memory** . Если изменяются оба параметра и значение параметра **index create memory** меньше значения **min memory per query**, то в системе отобразится предупреждающее сообщение, но это значение будет установлено. При выполнении запроса система выдаст такое же сообщение.  
  
-   При использовании секционированных таблиц и индексов требования к минимальному объему памяти для создания индексов могут быть значительно увеличены при наличии несвязанных секционированных индексов и большой степени параллелизма. Этот параметр управляет общим начальным объемом памяти, выделенным для всех секций индекса в одной операции создания индекса. Если объем, установленный данным параметром меньше, чем минимально необходимый для выполнения запроса, то выполнение запроса прервется с сообщением об ошибке.  
  
-   Рабочее значение этого параметра не будет превышать фактический объем памяти, используемый операционной системой и платформой оборудования, на которой выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В 32-разрядных версиях операционных систем это значение не превышает 3 гигабайт (ГБ).  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Параметр **index create memory** настраивается автоматически, и, как правило, дополнительная настройка не требуется. Однако при возникновении затруднений при создании индексов можно попробовать увеличить значение этого параметра.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-index-create-memory-option"></a>Настройка параметра index create memory  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Память** .  
  
3.  В свойстве **Память для создания индекса**введите или выберите необходимое значение параметра.  
  
     Параметр **index create memory** предназначен для управления объемом памяти, используемой операциями сортировки при создании индексов. Параметр **Память при создании индекса** конфигурируется автоматически, и в большинстве случаев его дополнительная настройка не требуется. Однако при возникновении затруднений при создании индексов можно попробовать увеличить значение этого параметра. Операции сортировки в запросах управляются параметром **min memory per query** .  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-index-create-memory-option"></a>Настройка параметра index create memory  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `index create memory` равным `4096`.  
  
```sql  
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
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-index-create-memory-option"></a><a name="FollowUp"></a> Продолжение: после настройки параметра index create memory  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [sys. Configurations &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера «Server Memory»](server-memory-server-configuration-options.md)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
