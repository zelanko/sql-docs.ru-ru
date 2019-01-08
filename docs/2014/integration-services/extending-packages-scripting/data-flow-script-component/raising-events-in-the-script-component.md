---
title: Вызов событий в компоненте скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 770b271c7614743c46a61b829858bf9ce63ece7d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376176"
---
# <a name="raising-events-in-the-script-component"></a>Вызов событий в компоненте скрипта
  События позволяют сообщать об ошибках и предупреждениях, а также передавать другие сведения, например о ходе выполнения задачи или ее состоянии, в пакет, содержащий задачу. Пакет предоставляет обработчики событий для управления уведомлениями о событиях. Компонент скрипта может формировать события путем вызова методов свойства <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> класса `ScriptMain`. Дополнительные сведения о том, как пакеты службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] обрабатывают события, см. в разделе [Обработчики событий в службах Integration Services (SSIS)](../../integration-services-ssis-event-handlers.md).  
  
 События могут регистрироваться любым регистратором, включенным в пакете. Регистраторы сохраняют сведения о событиях в хранилище данных. Компонент скрипта также может использовать метод <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> для записи данных в регистратор, не формируя событий. Дополнительные сведения об использовании метода <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> см. в следующем разделе.  
  
 Для формирования события задача «Скрипт» вызывает один из следующих методов интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> свойства <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A>:  
  
|Событие|Описание|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>|Вызывает в пакете определяемое пользователем событие.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A>|Извещает пакет об ошибке.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>|Передает сведения пользователю.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireProgress%2A>|Информирует пакет о ходе выполнения компонента.|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A>|Информирует пакет о том, что компонент находится в состоянии, требующем уведомления пользователя, но не являющемся ошибкой.|  
  
 Ниже приведен простой пример формирования события ошибки:  
  
 `Dim myMetadata as IDTSComponentMetaData100`  
  
 `myMetaData = Me.ComponentMetaData`  
  
 `myMetaData.FireError(...)`  
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Обработчики событий в службах Integration Services (SSIS)](../../integration-services-ssis-event-handlers.md)   
 [Добавление обработчика событий к пакету](../../add-an-event-handler-to-a-package.md)  
  
  
