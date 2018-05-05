---
title: 'Шаг 5: DataControl годным внесенные (учебник служб удаленных рабочих СТОЛОВ) | Документы Microsoft'
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 564c9b1984226c02ab1cb960ff6e4ed32b5527d8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>Шаг 5: DataControl годным внесенные (учебник служб удаленных рабочих СТОЛОВ)
Возвращенный **записей** объект доступен для использования. Проверьте, перехода или изменить его, как и любой другой **записей**. Что делать с **записей** зависит от среды. Visual Basic и Visual C++ имеют визуальные элементы управления, которые могут использовать **записей** прямо или косвенно с помощью элемента управления Включение данных.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Например, при отображении веб-страницы в Microsoft Internet Explorer, может потребоваться отобразить **записей** данных в элементе управления визуального объекта. Визуальные элементы управления на веб-странице не может получить доступ к **записей** объекта напрямую. Тем не менее, они могут получить доступ **записей** посредством [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md). **RDS. DataControl** был готов к использованию с помощью visual управления его [SourceRecordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) свойству **записей** объекта.  
  
 Объект визуального элемента управления должен иметь его **DATASRC** равным **RDS. DataControl**и его **DATAFLD** свойство **записей** объекта поля (столбца).  
  
 В этом учебнике значение **SourceRecordset** свойства:  
  
```  
Sub RDSTutorial5()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DC as New RDS.DataControl  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "http://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
   DC.SourceRecordset = RS         ' Visual controls can now bind to DC.  
...  
```  
  
## <a name="see-also"></a>См. также  
 [Шаг 6: Изменения будут отправлены на сервер (учебник служб удаленных рабочих СТОЛОВ)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
