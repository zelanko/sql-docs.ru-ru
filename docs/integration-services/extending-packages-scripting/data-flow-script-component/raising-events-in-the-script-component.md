---
title: Вызов событий в компоненте скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e8efead59cd24cbe2e556991b4a7699be980c544
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713242"
---
# <a name="raising-events-in-the-script-component"></a>Вызов событий в компоненте скрипта
  События позволяют сообщать об ошибках и предупреждениях, а также передавать другие сведения, например о ходе выполнения задачи или ее состоянии, в пакет, содержащий задачу. Пакет предоставляет обработчики событий для управления уведомлениями о событиях. Компонент скрипта может формировать события путем вызова методов свойства <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> класса **ScriptMain**. Дополнительные сведения о том, как пакеты службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] обрабатывают события, см. в разделе [Обработчики событий в службах Integration Services (SSIS)](../../../integration-services/integration-services-ssis-event-handlers.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Обработчики событий в службах Integration Services (SSIS)](../../../integration-services/integration-services-ssis-event-handlers.md)   
 [Добавление обработчика событий к пакету](http://msdn.microsoft.com/library/5e56885d-8658-480a-bed9-3f2f8003fd78)  
  
  
