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
ms.openlocfilehash: e27580790e0bf9742ad869de7e42439d0b7f3fe6
ms.sourcegitcommit: 0ea19d8e3bd9d91a416311e00a5fb0267d41949e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2019
ms.locfileid: "71174297"
---
# <a name="sp_send_dbmail-transact-sql"></a>Хранимая процедура sp_send_dbmail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Отправляет сообщение электронной почты указанным получателям. Сообщение может включать результирующий набор запроса, файлы вложений или и то, и другое. Когда почта успешно помещается в очередь Database Mail, процедура **sp_send_dbmail** возвращает **mailitem_id** сообщения. Эта хранимая процедура находится в базе данных **msdb** .  
  
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
`[ @profile_name = ] 'profile_name'`Имя профиля, из которого отправляется сообщение. *Profile_name* имеет тип **sysname**и значение по умолчанию NULL. *Profile_name* должно быть именем существующего профиля Database Mail. Если *profile_name* не указан, то процедура **sp_send_dbmail** использует для текущего пользователя частный профиль по умолчанию. Если у пользователя нет частного профиля по умолчанию, то процедура **sp_send_dbmail** использует открытый профиль по умолчанию для базы данных **msdb** . Если у пользователя нет личного профиля по умолчанию и нет открытого профиля по умолчанию для базы данных,  **\@** необходимо указать profile_name.  
  
`[ @recipients = ] 'recipients'`Разделенный точками с запятой список адресов электронной почты, на которые отправляется сообщение. Список получателей имеет тип **varchar (max)** . Хотя этот параметр является необязательным, должен быть указан хотя бы один из  **\@получателей**,  **\@copy_recipients**или  **\@blind_copy_recipients** , или процедура **sp_send_dbmail** возвращает ошибку.  
  
`[ @copy_recipients = ] 'copy_recipients'`Разделенный точками с запятой список адресов электронной почты, в которые копируется сообщение. Список получателей копии имеет тип **varchar (max)** . Хотя этот параметр является необязательным, должен быть указан хотя бы один из  **\@получателей**,  **\@copy_recipients**или  **\@blind_copy_recipients** , или процедура **sp_send_dbmail** возвращает ошибку.  
  
`[ @blind_copy_recipients = ] 'blind_copy_recipients'`Разделенный точками с запятой список адресов электронной почты, на которые скрыта копия сообщения. Список получателей копии "вслепую" имеет тип **varchar (max)** . Хотя этот параметр является необязательным, должен быть указан хотя бы один из  **\@получателей**,  **\@copy_recipients**или  **\@blind_copy_recipients** , или процедура **sp_send_dbmail** возвращает ошибку.  
  
`[ @from_address = ] 'from_address'`Значение адреса отчасти сообщения электронной почты. Это необязательный параметр, используемый для переопределения параметров в профиле электронной почты. Этот параметр имеет тип **varchar (max)** . Параметры безопасности SMTP определяют, будет ли принято переопределение настроек. Если параметр не указан, значение по умолчанию равно NULL.  
  
`[ @reply_to = ] 'reply_to'`Значение параметра "ответить на адрес" сообщения электронной почты. В качестве допустимого значения принимается только один адрес электронной почты. Это необязательный параметр, используемый для переопределения параметров в профиле электронной почты. Этот параметр имеет тип **varchar (max)** . Параметры безопасности SMTP определяют, будет ли принято переопределение настроек. Если параметр не указан, значение по умолчанию равно NULL.  
  
`[ @subject = ] 'subject'`Тема сообщения электронной почты. Тема имеет тип **nvarchar (255)** . Если тема не указана, то по умолчанию устанавливается «Сообщение SQL Server».  
  
`[ @body = ] 'body'`Текст сообщения электронной почты. Текст сообщения имеет тип **nvarchar (max)** и значение по умолчанию NULL.  
  
`[ @body_format = ] 'body_format'`Формат текста сообщения. Параметр имеет тип **varchar (20)** и значение по умолчанию NULL. Если установлено значение этого аргумента, то устанавливаются заголовки исходящих сообщений, что указывает на формат текста сообщения. Аргумент может содержать одно из следующих значений.  
  
-   TEXT  
  
-   HTML  
  
 По умолчанию имеет значение TEXT.  
  
`[ @importance = ] 'importance'`Важность сообщения. Параметр имеет тип **varchar (6)** . Аргумент может содержать одно из следующих значений.  
  
-   Низкий  
  
-   Нормальный  
  
-   Высокий  
  
 По умолчанию имеет значение Normal.  
  
`[ @sensitivity = ] 'sensitivity'`Чувствительность сообщения. Параметр имеет тип **varchar (12)** . Аргумент может содержать одно из следующих значений.  
  
-   Нормальный  
  
-   Personal  
  
-   Private  
  
-   Confidential  
  
 По умолчанию имеет значение Normal.  
  
`[ @file_attachments = ] 'file_attachments'`Разделенный точками с запятой список имен файлов, которые нужно присоединить к сообщению электронной почты. Файлы в списке должны указываться как абсолютные пути. Список вложений имеет тип **nvarchar (max)** . По умолчанию компонент Database Mail ограничивает размер файлов вложений до 1 МБ на файл.  
 
 > [!IMPORTANT]
 > Этот параметр недоступен в Управляемый экземпляр Azure SQL, так как он не может получить доступ к локальной файловой системе.
  
`[ @query = ] 'query'`Запрос для выполнения. Результаты запроса могут прикрепляться в виде файла или включаться в текст сообщения электронной почты. Запрос имеет тип **nvarchar (max)** и может содержать любые допустимые [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции. Обратите внимание, что запрос выполняется в отдельном сеансе, поэтому локальные переменные в скрипте, вызвавшем процедуру **sp_send_dbmail** , недоступны для запроса.  
  
`[ @execute_query_database = ] 'execute_query_database'`Контекст базы данных, в котором хранимая процедура выполняет запрос. Параметр имеет тип **sysname**и значение по умолчанию текущей базы данных. Этот параметр применим только в том  **\@** случае, если указан запрос.  
  
`[ @attach_query_result_as_file = ] attach_query_result_as_file`Указывает, возвращается ли результирующий набор запроса в виде вложенного файла. *attach_query_result_as_file* имеет тип **bit**и значение по умолчанию 0.  
  
 Если значение равно 0, результаты запроса включаются в текст сообщения электронной почты после содержимого  **\@параметра Body** . Если установлено значение 1, то результаты возвращаются в виде вложения. Этот параметр применим только в том  **\@** случае, если указан запрос.  
  
`[ @query_attachment_filename = ] query_attachment_filename`Указывает имя файла, используемого для результирующего набора вложения запроса. *query_attachment_filename* имеет тип **nvarchar (255)** и значение по умолчанию NULL. Этот параметр игнорируется, если *attach_query_result* имеет значение 0. Если значение *attach_query_result* равно 1 и этот параметр имеет значение NULL, Database Mail создает произвольное имя файла.  
  
`[ @query_result_header = ] query_result_header`Указывает, содержат ли результаты запроса заголовки столбцов. Значение query_result_header имеет тип **bit**. Если значение равно 1, результаты запроса содержат заголовки столбцов. Если установлено значение 0, то результаты запроса не содержат заголовков столбцов. По умолчанию этот параметр имеет значение **1**. Этот параметр применим только в том  **\@** случае, если указан запрос.  
 
   >[!NOTE]
   > Следующая ошибка может возникать при задании значения @query_result_header 0 и задании значения @query_no_truncate 1:
   > <br> Сообщение 22050, уровень 16, состояние 1, строка 12: Не удалось инициализировать библиотеку sqlcmd, номер ошибки — 2147024809.
  
`[ @query_result_width = ] query_result_width`Толщина линии (в символах), используемой для форматирования результатов запроса. *Query_result_width* имеет тип **int**и значение по умолчанию 256. Его значение должно находиться в диапазоне от 10 до 32767. Этот параметр применим только в том  **\@** случае, если указан запрос.  
  
`[ @query_result_separator = ] 'query_result_separator'`Символ, используемый для разделения столбцов в выходных данных запроса. Разделитель имеет тип **char (1)** . Значением по умолчанию является '  ' (пробел).  
  
`[ @exclude_query_output = ] exclude_query_output`Указывает, следует ли возвращать результат выполнения запроса в сообщении электронной почты. **exclude_query_output** имеет бит и значение по умолчанию 0. Если этот параметр равен 0, то при выполнении хранимой процедуры **sp_send_dbmail** выводится сообщение, возвращенное в результате выполнения запроса на консоли. Если этот параметр равен 1, выполнение хранимой процедуры **sp_send_dbmail** не выводит сообщения о выполнении запроса в консоли.  
  
`[ @append_query_error = ] append_query_error`Указывает, следует ли отправлять сообщение электронной почты, когда ошибка возвращается из запроса, указанного  **\@** в аргументе запроса. **append_query_error** имеет **бит**и значение по умолчанию 0. Если аргумент принимает значение 1, то компонент Database Mail посылает сообщение электронной почты и включает сообщение об ошибке запроса в текст сообщения электронной почты. Если этот параметр равен 0, Database Mail не отправляет сообщение электронной почты, а процедура **sp_send_dbmail** завершается с кодом возврата 1, что означает сбой.  
  
`[ @query_no_truncate = ] query_no_truncate`Указывает, следует ли выполнять запрос с параметром, который позволяет избежать усечения типов данных с большими переменными длиной (**varchar (max)** , **nvarchar (max)** , **varbinary (max)** , **XML**, **Text**, **ntext**, **Image**, и определяемые пользователем типы данных). Если значение этого аргумента установлено, то результаты запроса не содержат заголовки столбцов. Значение *query_no_truncate* имеет тип **bit**. Если установлено значение 0 или не установлено вовсе, то столбцы в запросе усекаются до 256 символов. Если установлено значение 1, то столбцы в запросе не усекаются. Данный аргумент по умолчанию принимает значение 0.  
  
> [!NOTE]  
>  При использовании с большими объемами данных параметр @**query_no_truncate** потребляет дополнительные ресурсы и может снизить производительность сервера.  
  
`[ @query_result_no_padding ] @query_result_no_padding`Тип — bit. Значение по умолчанию равно 0. Если задано значение 1, результаты запроса не дополняются, что может привести к уменьшению размера файла. Если задано @query_result_no_padding значение 1 и @query_result_width задан параметр, @query_result_no_padding параметр перезаписывает @query_result_width параметр.  
  
 Ошибки при этом не возникает.  
 
  >[!NOTE]
  > Следующая ошибка может возникнуть при установке значения @query_result_no_padding 1 и предоставлении параметра для@query_no_truncate:
  > <br> Сообщение 22050, уровень 16, состояние 1, строка 0: Не удалось выполнить запрос, так как @query_result_no_append параметры @query_no_truncate и являются взаимоисключающими. 
  
 Если задать @query_result_no_padding значение 1 и @query_no_truncate задать параметр, будет выдана ошибка.  
  
`[ @mailitem_id = ] mailitem_id [ OUTPUT ]`Необязательный выходной параметр возвращает *mailitem_id* сообщения. *Mailitem_id* имеет тип **int**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Код возврата 0 означает успешное завершение. Любое другое значение означает неуспешное завершение. Код ошибки для инструкции, которая завершилась ошибкой, хранится в переменной@ERROR @.  
  
## <a name="result-sets"></a>Результирующие наборы  
 В случае успешного выполнения возвращает сообщение «Письмо поставлено в очередь».  
  
## <a name="remarks"></a>Примечания  
 Перед использованием Database Mail необходимо включить с помощью мастера настройки Database Mail или **sp_configure**.  
  
 **sysmail_stop_sp** прекращает Database Mail, останавливая Service Broker объекты, используемые внешней программой. Процедура **sp_send_dbmail** по-прежнему принимает почту, когда Database Mail остановлена с помощью **sysmail_stop_sp**. Чтобы запустить Database Mail, используйте **sysmail_start_sp**.  
  
 Если  **\@профиль** не указан, то в процессе **sp_send_dbmail** используется профиль по умолчанию. Если пользователь, отсылающий электронное сообщение, имеет личный профиль по умолчанию, то компонент Database Mail использует этот профиль. Если у пользователя нет личного профиля по умолчанию, то процедура **sp_send_dbmail** использует открытый профиль по умолчанию. Если нет личного профиля по умолчанию для пользователя и открытого профиля по умолчанию, то процедура **sp_send_dbmail** возвращает ошибку.  
  
 Процедура **sp_send_dbmail** не поддерживает сообщения электронной почты без содержимого. Чтобы отправить сообщение электронной почты, необходимо указать хотя бы один  **\@текст**,  **\@запрос**,  **\@file_attachments**или  **\@тему**. В противном случае процедура **sp_send_dbmail** возвращает ошибку.  
  
 Для контроля доступа к файлам компонент Database Mail использует контекст безопасности [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows текущего пользователя. Поэтому пользователи, прошедшие [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверку подлинности, не могут вкладывать файлы с помощью  **\@file_attachments**. Windows не позволяет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставлять учетные данные одного удаленного компьютера другому. Поэтому компонент Database Mail не сможет прикрепить файлы из общего сетевого ресурса в случаях, когда команда запускается не с того компьютера, на котором работает служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если указаны как  **\@Query** и  **\@file_attachments** , так и файл не удается найти, запрос по-прежнему выполняется, но сообщение электронной почты не отправляется.  
  
 Если указывается запрос, то результирующий набор форматируется как встроенный текст. В результате двоичные данные посылаются в шестнадцатеричном формате.  
  
 **Параметры\@Recipients**,  **\@copy_recipients**и  **blind_copy_recipients—этоспискиадресовэлектроннойпочты,разделенныеточкойсзапятой.\@** Необходимо указать хотя бы один из этих параметров, иначе процедура **sp_send_dbmail** возвращает ошибку.  
  
 При выполнении процедуры **sp_send_dbmail** без контекста транзакции Database Mail запускает и фиксирует неявную транзакцию. При выполнении процедуры **sp_send_dbmail** в существующей транзакции Database Mail полагается на пользователя на фиксацию или откат изменений. Вложенные транзакции не запускаются.  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение процедуры **sp_send_dbmail** по умолчанию для всех членов роли базы данных **датабасемаилусер** в базе данных **msdb** . Однако, когда пользователь, отправляющий сообщение, не имеет разрешения на использование профиля для запроса, процедура **sp_send_dbmail** возвращает ошибку и не отправляет сообщение.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-sending-an-e-mail-message"></a>A. Отправка сообщения электронной почты  
 В этом примере для вашего друга отправляется сообщение электронной почты с помощью `myfriend@Adventure-Works.com`адреса электронной почты. Сообщение имеет тему `Automated Success Message`. Текст сообщения содержит предложение `'The stored procedure finished successfully'`.  
  
```  
EXEC msdb.dbo.sp_send_dbmail  
    @profile_name = 'Adventure Works Administrator',  
    @recipients = 'yourfriend@Adventure-Works.com',  
    @body = 'The stored procedure finished successfully.',  
    @subject = 'Automated Success Message' ;  
```  
  
### <a name="b-sending-an-e-mail-message-with-the-results-of-a-query"></a>Б. Отправка сообщения электронной почты с результатами запроса  
 В этом примере для вашего друга отправляется сообщение электронной почты с помощью `yourfriend@Adventure-Works.com`адреса электронной почты. Сообщение имеет тему `Work Order Count` и выполняет запрос, который показывает количество заявок на выполнение работ с меньшим `DueDate`, чем через два дня после 30 апреля 2004 г. Компонент Database Mail прикрепляет результаты в виде текстового файла.  
  
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
 В этом примере для вашего друга отправляется сообщение электронной почты с помощью `yourfriend@Adventure-Works.com`адреса электронной почты. Сообщение имеет тему `Work Order List` и содержит документ HTML, который показывает количество заявок на выполнение работ с меньшим сроком `DueDate`, чем через два дня после 30 апреля 2004 г. Компонент Database Mail посылает результаты в формате HTML.  
  
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
 [Database Mail объекты конфигурации](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Database Mail хранимых &#40;процедур TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)  
  
  
