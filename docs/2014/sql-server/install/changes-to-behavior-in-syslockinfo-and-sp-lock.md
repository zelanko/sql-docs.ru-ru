---
title: Изменения в работе представления syslockinfo и процедуры sp_lock | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 982f31bbffb32726089fa331d105bfc262fc16a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097841"
---
# <a name="changes-to-behavior-in-syslockinfo-and-splock"></a>Изменение в работе представления syslockinfo и процедуры sp_lock
  Представление**syslockinfo** и хранимая процедура **sp_lock** могут возвратить непредвиденные значения. Кроме того, они могут вернуть дополнительные строки, в то время как предыдущие версии представления **syslockinfo** и хранимой процедуры **sp_lock** возвращали не более двух строк на каждый ресурс блокировки.  
  
 Для доступа к информации представления **syslockinfo** или запуска хранимой процедуры **sp_lock** необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **rsc_objid** и **rsc_indid** столбцы в **syslockinfo** и **objid** и **indid**  столбцы в **sp_lock** возвращают идентификатор объекта и идентификатор индекса. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] может быть возвращено нулевое значение.  
  
 В [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **syslockinfo** и **sp_lock** возвращать не более двух строк на каждый отдельный ресурс блокировки в одной транзакции. Начиная с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], если включено секционирование блокировок, может быть возвращено несколько строк для одного и того же ресурса, выполняющегося в рамках одной транзакции. Может быть до N + 1 строк возвращено, где N — число процессоров. Кроме того, теперь запросы GRANTED и WAITING могут отображаться для одного ресурса, что было невозможно в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
