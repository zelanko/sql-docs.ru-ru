---
title: sp_send_dbmail (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sendmail_sp_TSQL
- sendmail_sp
- SP_SEND_DBMAIL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_send_dbmail
ms.assetid: f1d7a795-a3fd-4043-ac4b-c781e76dab47
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b0eed101b1b336997b7f90c17b3f1471d4ea526b
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528307"
---
# <a name="spsenddbmail-transact-sql"></a>Хранимая процедура sp_send_dbmail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отправляет сообщение электронной почты указанным получателям. Сообщение может включать результирующий набор запроса, файлы вложений или и то, и другое. Если почта успешно поставлена в очередь компонента Database Mail, **sp_send_dbmail** возвращает **mailitem_id** сообщения. Эта хранимая процедура находится в **msdb** базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_send_dbmail [ [ @profile_name = ] 'profile_name' ]  
    [ , [ @recipients = ] 'recipients [ ; ...n ]' ]  
    [ , [ @copy_recipients = ] 'copy_recipient [ ; ...n ]' ]  
    [ , [ @blind_copy_recipients = ] 'blind_copy_recipient [ ; ...n ]' ]  
    [ , [ @from_address = ] 'from_address' ]  
    [ , [ @reply_to = ] 'reply_to' ]   
    [ , [ @subject = ] 'subject' ]   
    [ , [ @body = ] 'body' ]   
    [ , [ @body_format = ] 'body_format' ]  
    [ , [ @importance = ] 'importance' ]  
    [ , [ @sensitivity = ] 'sensitivity' ]  
    [ , [ @file_attachments = ] 'attachment [ ; ...n ]' ]  
    [ , [ @query = ] 'query' ]  
    [ , [ @execute_query_database = ] 'execute_query_database' ]  
    [ , [ @attach_query_result_as_file = ] attach_query_result_as_file ]  
    [ , [ @query_attachment_filename = ] query_attachment_filename ]  
    [ , [ @query_result_header = ] query_result_header ]  
    [ , [ @query_result_width = ] query_result_width ]  
    [ , [ @query_result_separator = ] 'query_result_separator' ]  
    [ , [ @exclude_query_output = ] exclude_query_output ]  
    [ , [ @append_query_error = ] append_query_error ]  
    [ , [ @query_no_truncate = ] query_no_truncate ]   
    [ , [ @query_result_no_padding = ] @query_result_no_padding ]   
    [ , [ @mailitem_id = ] mailitem_id ] [ OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @profile_name = ] 'profile_name'` — Имя профиля для отправки сообщений. *Profile_name* имеет тип **sysname**, значение по умолчанию NULL. *Profile_name* должно быть именем существующего профиля компонента Database Mail. Если аргумент *profile_name* указано, **sp_send_dbmail** использует личный профиль по умолчанию для текущего пользователя. Если пользователь не имеет личный профиль по умолчанию **sp_send_dbmail** использует открытый профиль по умолчанию для **msdb** базы данных. Если у пользователя нет личного профиля по умолчанию и нет ни открытого профиля по умолчанию для базы данных, **@profile_name** должен быть указан.  
  
`[ @recipients = ] 'recipients'` — Это список разделенных точкой с запятой адресов электронной почты для отправки сообщения. Список получателей относится тип **varchar(max)**. Несмотря на то, что этот параметр является необязательным, по крайней мере один из **@recipients**, **@copy_recipients**, или **@blind_copy_recipients** должен быть указан, или **sp_ send_dbmail** возвращает сообщение об ошибке.  
  
`[ @copy_recipients = ] 'copy_recipients'` — Это разделенный точками с запятой список адресов электронной почты для получателей копии сообщения. Список получателей копий имеет тип **varchar(max)**. Несмотря на то, что этот параметр является необязательным, по крайней мере один из **@recipients**, **@copy_recipients**, или **@blind_copy_recipients** должен быть указан, или **sp_ send_dbmail** возвращает сообщение об ошибке.  
  
`[ @blind_copy_recipients = ] 'blind_copy_recipients'` — Это разделенный точками с запятой список адресов электронной почты для получателей скрытой копии сообщения. Список получателей скрытых копий имеет тип **varchar(max)**. Несмотря на то, что этот параметр является необязательным, по крайней мере один из **@recipients**, **@copy_recipients**, или **@blind_copy_recipients** должен быть указан, или **sp_ send_dbmail** возвращает сообщение об ошибке.  
  
`[ @from_address = ] 'from_address'` Имеет значение «адрес отправителя» сообщения электронной почты. Это необязательный параметр, используемый для переопределения параметров в профиле электронной почты. Этот параметр имеет тип **varchar(MAX)**. Параметры безопасности SMTP определяют, будет ли принято переопределение настроек. Если параметр не указан, значение по умолчанию равно NULL.  
  
`[ @reply_to = ] 'reply_to'` Значение параметра «обратный адрес» сообщения электронной почты. В качестве допустимого значения принимается только один адрес электронной почты. Это необязательный параметр, используемый для переопределения параметров в профиле электронной почты. Этот параметр имеет тип **varchar(MAX)**. Параметры безопасности SMTP определяют, будет ли принято переопределение настроек. Если параметр не указан, значение по умолчанию равно NULL.  
  
`[ @subject = ] 'subject'` Является темой сообщения электронной почты. Субъект имеет тип **nvarchar(255)**. Если тема не указана, то по умолчанию устанавливается «Сообщение SQL Server».  
  
`[ @body = ] 'body'` Представляет собой тело сообщения электронной почты. Текст сообщения имеет тип **nvarchar(max)**, значение по умолчанию NULL.  
  
`[ @body_format = ] 'body_format'` — Это формат тела сообщения. Параметр имеет тип **varchar(20)**, значение по умолчанию NULL. Если установлено значение этого аргумента, то устанавливаются заголовки исходящих сообщений, что указывает на формат текста сообщения. Аргумент может содержать одно из следующих значений.  
  
-   TEXT  
  
-   HTML  
  
 По умолчанию имеет значение TEXT.  
  
`[ @importance = ] 'importance'` Является важность сообщения. Параметр имеет тип **varchar(6)**. Аргумент может содержать одно из следующих значений.  
  
-   Низкий  
  
-   Нормальный  
  
-   Высокий  
  
 По умолчанию имеет значение Normal.  
  
`[ @sensitivity = ] 'sensitivity'` Является Пометка сообщения. Параметр имеет тип **varchar(12)**. Аргумент может содержать одно из следующих значений.  
  
-   Нормальный  
  
-   Personal  
  
-   Private  
  
-   Confidential  
  
 По умолчанию имеет значение Normal.  
  
`[ @file_attachments = ] 'file_attachments'` — Это разделенный точками с запятой список имен файлов для вложения в сообщение электронной почты. Файлы в списке должны указываться как абсолютные пути. В списке вложения имеет тип **nvarchar(max)**. По умолчанию компонент Database Mail ограничивает размер файлов вложений до 1 МБ на файл.  
  
`[ @query = ] 'query'` Представляет собой запрос для выполнения. Результаты запроса могут прикрепляться в виде файла или включаться в текст сообщения электронной почты. Запрос имеет тип **nvarchar(max)** и может содержать любые допустимые [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций. Обратите внимание на то, что запрос выполняется в отдельном сеансе, так что локальные переменные в скрипте, вызываемом **sp_send_dbmail** недоступны для запроса.  
  
`[ @execute_query_database = ] 'execute_query_database'` Является контекст базы данных, в котором хранимая процедура выполняется запрос. Параметр имеет тип **sysname**, значение по умолчанию из текущей базы данных. Этот параметр применяется, только если **@query** указан.  
  
`[ @attach_query_result_as_file = ] attach_query_result_as_file` Указывает, возвращается ли результирующий набор запроса как прикрепленный файл. *attach_query_result_as_file* имеет тип **бит**, значение по умолчанию 0.  
  
 Если значение равно 0, результаты запроса включаются в тело сообщения электронной почты после содержимого **@body** параметра. Если установлено значение 1, то результаты возвращаются в виде вложения. Этот параметр применяется, только если **@query** указан.  
  
`[ @query_attachment_filename = ] query_attachment_filename` Указывает имя файла для результирующего набора вложения запроса. *query_attachment_filename* имеет тип **nvarchar(255)**, значение по умолчанию NULL. Этот параметр учитывается при *attach_query_result* равно 0. Когда *attach_query_result* составляет 1, этот параметр имеет значение NULL, компонент Database Mail создает произвольное имя файла.  
  
`[ @query_result_header = ] query_result_header` Указывает, включают ли результаты запроса заголовки столбцов. Query_result_header имеет тип **бит**. Если значение равно 1, результаты запроса содержат заголовки столбцов. Если установлено значение 0, то результаты запроса не содержат заголовков столбцов. Значение по умолчанию **1**. Этот параметр применяется, только если **@query** указан.  
 
   >[!NOTE]
   > Может возникнуть следующая ошибка при задании @query_result_header 0 и присвоения @query_no_truncate 1:
   > <br> Сообщение 22050, уровень 16, состояние 1, строка 12: Не удалось инициализировать библиотеку sqlcmd с номером ошибки -2147024809.
  
`[ @query_result_width = ] query_result_width` — Это Толщина линии, в символах для использования при форматировании результатов запроса. *Query_result_width* имеет тип **int**, значение по умолчанию 256. Его значение должно находиться в диапазоне от 10 до 32767. Этот параметр применяется, только если **@query** указан.  
  
`[ @query_result_separator = ] 'query_result_separator'` Символ, используемый для разделения столбцов в выходных данных запроса. Разделитель имеет тип **char(1)**. Значением по умолчанию является '  ' (пробел).  
  
`[ @exclude_query_output = ] exclude_query_output` Указывает, следует ли возвращать результат выполнения запроса в сообщение электронной почты. **exclude_query_output** имеет тип bit и значение по умолчанию 0. Если данный аргумент принимает 0, то выполнение **sp_send_dbmail** хранимая процедура печатает сообщение, возвращенное в результате выполнения запроса на консоли. Если этот параметр равен 1, выполнение **sp_send_dbmail** хранимой процедуры не выводятся на печать сообщения выполнения запроса на консоли.  
  
`[ @append_query_error = ] append_query_error` Указывает, следует ли отправлять сообщение электронной почты, если запрос, указанный в ошибку **@query** аргумент. **append_query_error** — **бит**, значение по умолчанию 0. Если аргумент принимает значение 1, то компонент Database Mail посылает сообщение электронной почты и включает сообщение об ошибке запроса в текст сообщения электронной почты. Если этот параметр равен 0, компонент Database Mail не отправляет сообщения электронной почты, и **sp_send_dbmail** заканчивается кодом возврата 1, что указывает на сбой.  
  
`[ @query_no_truncate = ] query_no_truncate` Указывает, следует ли выполнение запроса с параметром, который предотвращает усечение типов данных большой переменной длины (**varchar(max)**, **nvarchar(max)**, **varbinary(max)** **xml**, **текст**, **ntext**, **изображение**и определяемые пользователем типы данных). Если значение этого аргумента установлено, то результаты запроса не содержат заголовки столбцов. *Query_no_truncate* значение имеет тип **бит**. Если установлено значение 0 или не установлено вовсе, то столбцы в запросе усекаются до 256 символов. Если установлено значение 1, то столбцы в запросе не усекаются. Данный аргумент по умолчанию принимает значение 0.  
  
> [!NOTE]  
>  При использовании с большими объемами данных, @**query_no_truncate** параметр занимает дополнительные ресурсы и может привести к снижению производительности.  
  
`[ @query_result_no_padding ] @query_result_no_padding` Тип — bit. Значение по умолчанию равно 0. Если присвоено значение 1, результаты запроса не предусмотрено, что размер файла. Если задать @query_result_no_padding 1 и задать @query_result_width параметра @query_result_no_padding параметр перезаписывает @query_result_width параметра.  
  
 Ошибки при этом не возникает.  
 
  >[!NOTE]
  > Может возникнуть следующая ошибка при задании @query_result_no_padding 1 и предоставляя параметр для @query_no_truncate:
  > <br> Сообщение 22050, уровень 16, состояние 1, строка 0: Не удалось выполнить запрос, так как @query_result_no_append и @query_no_truncate параметры являются взаимно исключающими. 
  
 Если задать @query_result_no_padding 1 и задать @query_no_truncate параметра, ошибка возникает.  
  
`[ @mailitem_id = ] mailitem_id [ OUTPUT ]` Необязательный выходной параметр возвращает *mailitem_id* сообщения. *Mailitem_id* имеет тип **int**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Код возврата 0 означает успешное завершение. Любое другое значение означает неуспешное завершение. Код ошибки для инструкций, которые не удалось хранится в @@ERROR переменной.  
  
## <a name="result-sets"></a>Результирующие наборы  
 В случае успешного выполнения возвращает сообщение «Письмо поставлено в очередь».  
  
## <a name="remarks"></a>Примечания  
 Перед использованием компонент Database Mail необходимо включить с помощью мастера настройки компонента Database Mail, или **sp_configure**.  
  
 **sysmail_stop_sp** останавливает компонент Database Mail, останавливая работу объектов компонента Service Broker, используемые внешней программой. **sp_send_dbmail** продолжает принимать почту, когда компонент Database Mail остановлен при помощи **sysmail_stop_sp**. Для запуска компонента Database Mail, используйте **sysmail_start_sp**.  
  
 Когда **@profile** не указан, **sp_send_dbmail** использует профиль по умолчанию. Если пользователь, отсылающий электронное сообщение, имеет личный профиль по умолчанию, то компонент Database Mail использует этот профиль. Если пользователь имеет нет личного профиля по умолчанию, **sp_send_dbmail** использует открытый профиль по умолчанию. Если нет ни личного профиля по умолчанию для пользователя, ни открытого профиля по умолчанию, **sp_send_dbmail** возвращает сообщение об ошибке.  
  
 **sp_send_dbmail** не поддерживает сообщения электронной почты без содержимого. Чтобы отправить сообщение электронной почты, необходимо указать хотя бы один из **@body**, **@query**, **@file_attachments**, или **@subject**. В противном случае **sp_send_dbmail** возвращает сообщение об ошибке.  
  
 Для контроля доступа к файлам компонент Database Mail использует контекст безопасности [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows текущего пользователя. Таким образом, пользователи проходят проверку подлинности с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности не удается присоединить файлы с помощью **@file_attachments**. Windows не позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставлять учетные данные одного удаленного компьютера другому. Поэтому компонент Database Mail не сможет прикрепить файлы из общего сетевого ресурса в случаях, когда команда запускается не с того компьютера, на котором работает служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если оба **@query** и **@file_attachments** указаны и не может найти файл, по-прежнему выполняется запрос, но не отправляется сообщение электронной почты.  
  
 Если указывается запрос, то результирующий набор форматируется как встроенный текст. В результате двоичные данные посылаются в шестнадцатеричном формате.  
  
 Параметры **@recipients**, **@copy_recipients**, и **@blind_copy_recipients** , разделенных точкой с запятой список адресов электронной почты. Необходимо указать по крайней мере одно из этих параметров, или **sp_send_dbmail** возвращает сообщение об ошибке.  
  
 При выполнении **sp_send_dbmail** без контекста транзакции, компонент Database Mail запускает и фиксирует неявные транзакции. При выполнении **sp_send_dbmail** из в существующей транзакции, компонент Database Mail использует пользователь фиксацию или откат всех изменений. Вложенные транзакции не запускаются.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение **sp_send_dbmail** по умолчанию ко всем членам **DatabaseMailUser** роли базы данных в **msdb** базы данных. Тем не менее, при отправке сообщения не у пользователя разрешение на использование профиля для запроса, **sp_send_dbmail** возвращает ошибку и не отправляет сообщение.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-sending-an-e-mail-message"></a>A. Отправка сообщения электронной почты  
 Этот пример отправляет сообщение электронной почты по адресу электронной почты получателю `myfriend@Adventure-Works.com`. Сообщение имеет тему `Automated Success Message`. Текст сообщения содержит предложение `'The stored procedure finished successfully'`.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @body = 'The stored procedure finished successfully.',  
    @subject = 'Automated Success Message' ;  
```  
  
### <a name="b-sending-an-e-mail-message-with-the-results-of-a-query"></a>Б. Отправка сообщения электронной почты с результатами запроса  
 Этот пример отправляет сообщение электронной почты по адресу электронной почты получателю `yourfriend@Adventure-Works.com`. Сообщение имеет тему `Work Order Count` и выполняет запрос, который показывает количество заявок на выполнение работ с меньшим `DueDate`, чем через два дня после 30 апреля 2004 г. Компонент Database Mail прикрепляет результаты в виде текстового файла.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @query = 'SELECT COUNT(*) FROM AdventureWorks2012.Production.WorkOrder  
                  WHERE DueDate > ''2004-04-30''  
                  AND  DATEDIFF(dd, ''2004-04-30'', DueDate) < 2' ,  
    @subject = 'Work Order Count',  
    @attach_query_result_as_file = 1 ;  
```  
  
### <a name="c-sending-an-html-e-mail-message"></a>В. Отправка сообщения электронной почты в формате HTML  
 Этот пример отправляет сообщение электронной почты по адресу электронной почты получателю `yourfriend@Adventure-Works.com`. Сообщение имеет тему `Work Order List` и содержит документ HTML, который показывает количество заявок на выполнение работ с меньшим сроком `DueDate`, чем через два дня после 30 апреля 2004 г. Компонент Database Mail посылает результаты в формате HTML.  
  
```  
DECLARE @tableHTML  NVARCHAR(MAX) ;  
  
SET @tableHTML =  
    N'<H1>Work Order Report</H1>' +  
    N'<table border="1">' +  
    N'<tr><th>Work Order ID</th><th>Product ID</th>' +  
    N'<th>Name</th><th>Order Qty</th><th>Due Date</th>' +  
    N'<th>Expected Revenue</th></tr>' +  
    CAST ( ( SELECT td = wo.WorkOrderID,       '',  
                    td = p.ProductID, '',  
                    td = p.Name, '',  
                    td = wo.OrderQty, '',  
                    td = wo.DueDate, '',  
                    td = (p.ListPrice - p.StandardCost) * wo.OrderQty  
              FROM AdventureWorks.Production.WorkOrder as wo  
              JOIN AdventureWorks.Production.Product AS p  
              ON wo.ProductID = p.ProductID  
              WHERE DueDate > '2004-04-30'  
                AND DATEDIFF(dd, '2004-04-30', DueDate) < 2   
              ORDER BY DueDate ASC,  
                       (p.ListPrice - p.StandardCost) * wo.OrderQty DESC  
              FOR XML PATH('tr'), TYPE   
    ) AS NVARCHAR(MAX) ) +  
    N'</table>' ;  
  
EXEC msdb.dbo.sp_send_dbmail @recipients='yourfriend@Adventure-Works.com',  
    @subject = 'Work Order List',  
    @body = @tableHTML,  
    @body_format = 'HTML' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Объекты конфигурации компонента Database Mail](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Хранимые процедуры Database Mail &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)  
  
  
