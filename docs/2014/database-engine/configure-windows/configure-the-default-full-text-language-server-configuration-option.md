---
title: Настройка параметра конфигурации сервера "язык полнотекстового поиска по умолчанию" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- default full-text language option
ms.assetid: 0fa8785b-0830-4a52-aff5-fcf8268b72fc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d98194f5dead58b738c39503445923d9df49be06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62787070"
---
# <a name="configure-the-default-full-text-language-server-configuration-option"></a>Настройка параметра конфигурации сервера «язык полнотекстового поиска по умолчанию»
  В этом разделе описывается настройка параметра конфигурации `default full-text language` сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или. [!INCLUDE[tsql](../../includes/tsql-md.md)] `default full-text language` Параметр задает значение языка по умолчанию для полнотекстовых индексов. Лингвистический анализ выполняется для всех данных с полнотекстовой индексацией и зависит от языка, в котором эти данные представлены. Значением по умолчанию для этого параметра является язык сервера. Для локализованной версии программа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает `default full-text language` параметр на язык сервера, если существует соответствующее совпадение. Для нелокализованной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр `default full-text language` по умолчанию имеет значение, соответствующее английскому языку.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра default full-text language с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра default full-text language](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Значение `default full-text language` параметра используется в полнотекстовом индексе, если для столбца не указан язык, используя параметр Language **language_term** в инструкциях CREATE FULLTEXT INDEX и ALTER FULLTEXT INDEX. Если установленный по умолчанию язык полнотекстового поиска не поддерживается или отсутствует пакет лингвистического анализа, операция CREATE или ALTER завершится ошибкой, а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вернет сообщение об указании недопустимого языка.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Для `default full-text language` параметра требуется значение LCID. Список поддерживаемых кодов LCID и соответствующих им языков см. в разделе [sys.fulltext_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql). Могут быть доступны также и другие языки, например, от независимых поставщиков программного обеспечения. Если не найден указанный диалект языка, средство полнотекстового поиска автоматически переключается на основной язык.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-default-full-text-language-option"></a>Настройка параметра default full-text language  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Дополнительно** .  
  
3.  На вкладке "Разное" с помощью параметра **Язык полнотекстового поиска по умолчанию** можно задать значение языка по умолчанию для полнотекстовых индексированных столбцов.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-default-full-text-language-option"></a>Настройка параметра default full-text language  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование хранимой процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для присвоения параметру `default full-text` значения "Голландский" (`1043`).  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'default full-text language', 1043 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра default full-text language  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [sys.fulltext_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CREATE FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [ALTER FULLTEXT INDEX (Transact-SQL)](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
