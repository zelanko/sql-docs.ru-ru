---
title: Настройка параметра конфигурации сервера "network packet size" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
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
ms.openlocfilehash: be854d2002692611289d401b4ad98cb63cf4a27b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68731112"
---
# <a name="configure-the-network-packet-size-server-configuration-option"></a>Настройка параметра конфигурации сервера network packet size
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  В этом разделе описываются способы настройки параметра конфигурации сервера **network packet size** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **network packet size** используется для установки размера пакета (в байтах), применяемого во всей сети. Пакеты — это фрагменты данных фиксированного размера, с помощью которых осуществляется передача запросов и ответов между клиентами и серверами. Размер пакетов по умолчанию составляет 4096 байт.  
  
> [!NOTE]  
>  Не изменяйте размер пакета, если нет уверенности в том, что это повысит производительность. Для большинства приложений оптимальным является размер пакета, установленный по умолчанию.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра network packet size с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра network packet size](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Максимальный размер сетевого пакета для шифрованных соединений составляет 16 383 байта.  
  
> [!NOTE]  
> Если функция MARS включена, поставщик SMUX добавляет в пакет 16-байтовый заголовок перед шифрованием SSL, уменьшая максимальный размер сетевого пакета до 16368 байт.
   
###  <a name="Recommendations"></a> Рекомендации  
  
-   Это расширенный параметр, и изменять его следует только опытным администраторам баз данных или сертифицированным по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] специалистам.  
  
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
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование хранимой процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `network packet size` равным `6500` байт.  
  
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
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра network packet size  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
