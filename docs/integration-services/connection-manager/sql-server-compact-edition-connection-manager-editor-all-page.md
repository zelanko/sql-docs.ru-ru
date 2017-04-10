---
title: "Редактор диспетчера соединений SQL Server Compact Edition (страница &#171;Все&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sqlmobileconnection.all.f1"
helpviewer_keywords: 
  - "редактор диспетчера соединений SQL Server Compact"
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Редактор диспетчера соединений SQL Server Compact Edition (страница &#171;Все&#187;)
  Диалоговое окно **Диспетчер соединений SQL Server Compact Edition** позволяет задать свойства для соединения с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 Дополнительные сведения о диспетчере соединений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact Edition см. в разделе [Диспетчер соединений SQL Server Compact Edition](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager.md).  
  
## Параметры  
 **Пороговое значение для автосжатия **  
 Укажите в виде процентов допустимый размер свободного пространства в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact перед запуском процесса автосжатия.  
  
 **Укрупнение блокировок по умолчанию**  
 Определите число блокировок базы данных, которые установит база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact, прежде чем попытается укрупнить блокировки.  
  
 **Время ожидания блокировок по умолчанию**  
 Укажите время по умолчанию (в миллисекундах) ожидания транзакцией блокировок базы данных.  
  
 **Интервал записи**  
 Определите интервал (в секундах) между записями данных на диск зафиксированными транзакциями.  
  
 **Идентификатор локали**  
 Задайте идентификатор локали (LCID) базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Максимальный размер буфера**  
 Определите максимальный объем памяти (в килобайтах), используемый базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact перед записью данных на диск.  
  
 **Максимальный размер базы данных**  
 Укажите максимальный размер (в мегабайтах) базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Режим**  
 Укажите файловый режим, в котором будет открываться база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact. Значение этого свойства по умолчанию равно **Чтение и запись**.  
  
 Параметр «Режим» имеет четыре значения, описанные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Только для чтения**|Определяет доступ к базе данных только для чтения.|  
|**Чтение и запись**|Назначает разрешения на чтение и запись базы данных.|  
|**Монопольно**|Задает монопольный доступ к базе данных.|  
|**Общий доступ на чтение**|Определяет возможность одновременного чтения базы данных другими пользователями.|  
  
 **Сохранять сведения о безопасности**  
 Определите, будет ли осуществляться возврат сведений о безопасности в виде части строки соединения. Значение по умолчанию этого параметра равно **False**.  
  
 **Каталог временных файлов**  
 Задайте расположение временных файлов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Источник данных**  
 Укажите имя базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
 **Пароль**  
 Введите пароль для базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact.  
  
## См. также  
 [Справочник по сообщениям об ошибках служб Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Редактор диспетчера подключений SQL Server Compact Edition (страница "Соединение")](../../integration-services/connection-manager/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  