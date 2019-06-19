---
title: Настройка параметра конфигурации сервера user options | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- global default for all users [SQL Server]
- users [SQL Server], global defaults
- user options option [SQL Server]
ms.assetid: cfed8f86-6bcf-4b90-88eb-9656e22d5dc5
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 6d9a4b5da604917262b8787d71a6bc068a6fc552
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66803302"
---
# <a name="configure-the-user-options-server-configuration-option"></a>Настройка параметра конфигурации сервера user options
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описано, как настроить параметр конфигурации сервера **user options** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **user options** задает глобальные параметры по умолчанию для всех пользователей. Список параметров обработки запросов по умолчанию создается на время сеанса работы пользователя. Параметр **user options** позволяет изменить значения по умолчанию параметров инструкции SET (в случае если настройки сервера по умолчанию не подходят).  
  
 Пользователь может заменить эти значения по умолчанию с помощью инструкцию SET. Для новых имен входа параметр **user options** можно настроить динамически. После изменения параметра **user options**в новых сеансах будут использоваться новые параметры. На текущие сеансы эти изменения не повлияют.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра конфигурации user options с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра конфигурации user options](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   В следующей таблице перечислены и описаны значения параметра **user options**. Не все значения конфигурации совместимы друг с другом. Например, параметры ANSI_NULL_DFLT_ON и ANSI_NULL_DFLT_OFF не могут быть установлены одновременно.  
  
    |Значение|Конфигурация|Описание|  
    |-----------|-------------------|-----------------|  
    |1|DISABLE_DEF_CNST_CHK|Управляет промежуточной или отложенной проверкой ограничений.|  
    |2|IMPLICIT_TRANSACTIONS|Для соединений сетевой библиотеки dblib управляет неявным запуском транзакции при выполнении инструкции. Установка IMPLICIT_TRANSACTIONS не влияет на соединения через ODBC или OLEDB.|  
    |4|CURSOR_CLOSE_ON_COMMIT|Управляет поведением курсора после выполнения операции фиксации.|  
    |8|ANSI_WARNINGS|Управляет усечением и значениями NULL в предупреждениях статистических вычислений.|  
    |16|ANSI_PADDING|Управляет заполнением переменных фиксированной длины.|  
    |32|ANSI_NULLS|Управляет обработкой значений NULL при использовании операторов равенства.|  
    |64|ARITHABORT|Завершает запрос, если во время выполнения запроса возникает ошибка переполнения или деления на нуль.|  
    |128|ARITHIGNORE|Возвращает значение NULL, если во время выполнения запроса возникла ошибка переполнения или деления на ноль.|  
    |256|QUOTED_IDENTIFIER|При вычислении выражения различает двойные и одинарные кавычки.|  
    |512|NOCOUNT|Выключает сообщение, которое возвращается в конце каждой инструкции и указывает количество затронутых строк.|  
    |1024|ANSI_NULL_DFLT_ON|Изменяет поведение сеанса по использованию ANSI-совместимости для поддержки значений NULL. Новые столбцы, которые определялись без явного указания поддержки значений NULL, допускают значения NULL.|  
    |2048|ANSI_NULL_DFLT_OFF|Изменяет поведение сеанса, чтобы не допустить использования ANSI-совместимости для поддержки значений NULL. Новые столбцы, которые определялись без явного указания поддержки значений NULL, не допускают значения NULL.|  
    |4096|CONCAT_NULL_YIELDS_NULL|При сцеплении значения NULL со строкой возвращается значение NULL.|  
    |8192|NUMERIC_ROUNDABORT|Формируется ошибка при потере точности в выражении.|  
    |16384|XACT_ABORT|Если при выполнении инструкции Transact-SQL возникла ошибка, то выполняется откат транзакции.|  
  
-   Битовые позиции в параметре **user options** совпадают с позициями в функции @@OPTIONS. Каждому соединению соответствует своя собственная функция @@OPTIONS, которая представляет собой окружение конфигурации. При входе в экземпляр \ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]пользователь получает окружение по умолчанию, где параметру **user options** присваивается значение функции @@OPTIONS. При выполнении инструкции SET для параметра **user options** изменяется соответствующее значение функции @@OPTIONS для сеанса. Все соединения, установленные после изменения этой установки, принимают новое значение.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-user-options-configuration-option"></a>Настройка параметра конфигурации user options  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Выберите узел **Соединения** .  
  
3.  В поле **Параметры соединения по умолчанию** выберите один или несколько атрибутов для настройки параметров обработки запросов по умолчанию для всех подключенных пользователей.  
  
     По умолчанию не настроен ни один из пользовательских параметров.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-user-options-configuration-option"></a>Настройка параметра конфигурации user options  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере показано, как с помощью хранимой процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) настроить значение параметра `user options` , чтобы изменить значение параметра сервера ANSI_WARNINGS.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'user options', 8 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра конфигурации user options  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
