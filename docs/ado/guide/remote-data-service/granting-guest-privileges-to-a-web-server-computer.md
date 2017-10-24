---
title: "Предоставление прав гостевой веб-сервере | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d9027a8e8adead5801a27465bda36a347472e383
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Предоставление прав гостевой веб-сервере
Учетная запись анонимного Web server (IUSR_*ComputerName*) должны добавляться к локальной группе гостей на компьютере веб-сервера для использования RDS.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Для предоставления прав гостевой веб-сервере  
  
1.  На компьютере Microsoft Windows 2000 Server нажмите кнопку **запустить**, пункты **программы**, пункты **Администрирование**и нажмите кнопку **компьютера Управление**.  
  
2.  В дереве консоли в **локальные пользователи и группы**, нажмите кнопку **группы**.  
  
3.  Выберите **гости** локальной группы. Из **действия** меню, выберите **свойства**.  
  
4.  В **свойства гости** диалоговое окно, нажмите кнопку **добавить**.  
  
5.  Если учетной записи анонимного Web server не отображается в списке в **Выбор пользователей или групп** диалогового окна введите его имя (IUSR_*ComputerName*) в нижней пустое поле и нажмите кнопку **добавить **.  
  
6.  Нажмите кнопку **ОК**.



