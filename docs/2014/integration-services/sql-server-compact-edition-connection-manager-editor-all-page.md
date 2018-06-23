---
title: SQL Server Compact редактор диспетчера соединений Edition (страница «все») | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.sqlmobileconnection.all.f1
helpviewer_keywords:
- SQL Server Compact Connection Manager Editor
ms.assetid: f9fbff4b-c502-44b3-8e7b-398d66e82206
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 72da9792c77970802a01aedccda6690ea1be2225
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193605"
---
# <a name="sql-server-compact-edition-connection-manager-editor-all-page"></a>Редактор диспетчера соединений SQL Server Compact Edition (страница «Все»)
  Диалоговое окно **Диспетчер соединений SQL Server Compact Edition** позволяет задать свойства для соединения с базой данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 Дополнительные сведения о диспетчере соединений [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact Edition см. в разделе [Диспетчер соединений SQL Server Compact Edition](connection-manager/sql-server-compact-edition-connection-manager.md).  
  
## <a name="options"></a>Параметры  
 **Пороговое значение для автосжатия**  
 Укажите в виде процентов допустимый размер свободного пространства в базе данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact перед запуском процесса автосжатия.  
  
 **Укрупнение блокировок по умолчанию**  
 Определите число блокировок базы данных, которые установит база данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact, прежде чем попытается укрупнить блокировки.  
  
 **Время ожидания блокировок по умолчанию**  
 Укажите время по умолчанию (в миллисекундах) ожидания транзакцией блокировок базы данных.  
  
 **Интервал записи**  
 Определите интервал (в секундах) между записями данных на диск зафиксированными транзакциями.  
  
 **Идентификатор локали**  
 Задайте идентификатор локали (LCID) базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Максимальный размер буфера**  
 Определите максимальный объем памяти (в килобайтах), используемый базой данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact перед записью данных на диск.  
  
 **Максимальный размер базы данных**  
 Укажите максимальный размер (в мегабайтах) базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Режим**  
 Укажите файловый режим, в котором будет открываться база данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact. Значение этого свойства по умолчанию равно **Чтение и запись**.  
  
 Параметр «Режим» имеет четыре значения, описанные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Только для чтения**|Определяет доступ к базе данных только для чтения.|  
|**Чтение и запись**|Назначает разрешения на чтение и запись базы данных.|  
|**Монопольно**|Задает монопольный доступ к базе данных.|  
|**Общий доступ на чтение**|Определяет возможность одновременного чтения базы данных другими пользователями.|  
  
 **Сохранять сведения о безопасности**  
 Определите, будет ли осуществляться возврат сведений о безопасности в виде части строки соединения. Значение по умолчанию этого параметра равно **False**.  
  
 **Каталог временных файлов**  
 Задайте расположение временных файлов базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Источник данных**  
 Укажите имя базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
 **Пароль**  
 Введите пароль для базы данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact.  
  
## <a name="see-also"></a>См. также  
 [Об ошибках служб Integration Services и справочник по сообщениям](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [SQL Server Compact редактор диспетчера соединений Edition &#40;страница «соединение»&#41;](../../2014/integration-services/sql-server-compact-edition-connection-manager-editor-connection-page.md)  
  
  