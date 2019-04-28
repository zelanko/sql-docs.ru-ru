---
title: Настройка параметра конфигурации сервера "network packet size" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default packet size
- size [SQL Server], packets
- packets [SQL Server], size
- network packet size option
ms.assetid: 236985bf-fc4a-4a57-98f7-a71ef977fd7b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4bd992f16158e7286db668256dc5963d83dbd4b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787003"
---
# <a name="configure-the-network-packet-size-server-configuration-option"></a>Настройка параметра конфигурации сервера network packet size
  В этом разделе описываются способы настройки `network packet size` параметр конфигурации сервера в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. `network packet size` Параметр задает размер пакета (в байтах), который используется во всей сети. Пакеты — это фрагменты данных фиксированного размера, с помощью которых осуществляется передача запросов и ответов между клиентами и серверами. Размер пакетов по умолчанию составляет 4096 байт.  
  
> [!NOTE]  
>  Не изменяйте размер пакета, если нет уверенности в том, что это повысит производительность. Для большинства приложений оптимальным является размер пакета, установленный по умолчанию.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра network packet size с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра network packet size](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Максимальный размер сетевого пакета для шифрованных соединений составляет 16 383 байта.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Если приложение осуществляет массовое копирование или отправляет/получает большие объемы данных типа text или image, увеличение размера пакета может повысить эффективность работы системы за счет сокращения числа сетевых операций чтения и записи. Если приложение отправляет и получает небольшие объемы информации, размер пакета можно уменьшить до 512 байт, чего в большинстве случаев достаточно.  
  
-   Если система работает с несколькими сетевыми протоколами, присвойте параметру network packet size значение, оптимальное для протокола, который используется чаще всего. Параметр network packet size позволяет повысить производительность сети, если сетевые протоколы поддерживают более крупные пакеты. Это значение может быть переопределено в клиентских приложениях.  
  
-   Для запроса на изменение размера пакета также используются функции OLE DB, ODBC и DB-Library. Если сервер не поддерживает запрошенный размер пакета, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] отправляет клиенту предупреждающее сообщение. В некоторых ситуациях изменение размера пакета может привести к ошибке в канале связи, например следующей:  
  
     `Native Error: 233, no process is on the other end of the pipe.`  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-network-packet-size-option"></a>Настройка параметра network packet size  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Дополнительно** .  
  
3.  На вкладке **Сеть**выберите значение в поле **Размер сетевого пакета** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-network-packet-size-option"></a>Настройка параметра network packet size  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование хранимой процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `network packet size` равным `6500` байт.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'network packet size', 6500 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра network packet size  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
