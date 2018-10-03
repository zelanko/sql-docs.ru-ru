---
title: Предоставление прав гостя для веб-сервере | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f0ebb888b223cab81d01817ec4c10f96813d3f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678482"
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Предоставление прав гостя для компьютера веб-сервера
Учетная запись анонимного Web server (IUSR_*ComputerName*) необходимо добавить к локальной группе гостей на компьютере веб-сервера для использования RDS.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Предоставление прав гостя для веб-сервере  
  
1.  На компьютере Microsoft Windows 2000 Server, нажмите кнопку **запустить**, пункты **программы**, пункты **Администрирование**и нажмите кнопку **компьютера Управление**.  
  
2.  В дереве консоли в **локальные пользователи и группы**, нажмите кнопку **группы**.  
  
3.  Выберите **гостей** локальной группы. Из **действие** меню, выберите **свойства**.  
  
4.  В **свойства гостей** диалоговом окне щелкните **добавить**.  
  
5.  Если учетной записи анонимного Web server не отображается в списке в **Выбор пользователей или групп** диалогового окна введите его имя (IUSR_*ComputerName*) в нижней пустое поле и нажмите кнопку **добавить** .  
  
6.  Нажмите кнопку **ОК**.


