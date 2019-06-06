---
title: Шаг 5. DataControl — можно использовать (учебник по RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS tutorial [ADO], datacontrol made usable
ms.assetid: ed5c4a24-9804-4c85-817e-317652acb9b4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f654bc1ccd913c5fc31f81cae67ffdb84e80f952
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704153"
---
# <a name="step-5-datacontrol-is-made-usable-rds-tutorial"></a>Шаг 5. DataControl теперь можно использовать (учебник по RDS)
Возвращенный **записей** объект доступен для использования. Можно изучать, перехода или его изменить, как любой другой **записей**. Что делать с **записей** зависит от среды. Visual Basic и Visual C++ имеют визуальные элементы управления, которые могут использовать **записей** прямо или косвенно с помощью элемента управления Включение данных.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Например, при отображении веб-страницы в Microsoft Internet Explorer, может потребоваться отобразить **записей** данные в элементе управления визуального объекта. Визуальные элементы управления веб-страницы не может получить доступ к **записей** объекта напрямую. Тем не менее, при доступе к **записей** объекта через [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md). **RDS. DataControl** становится доступным, визуальный элемент управления его [SourceRecordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) свойству **набор записей** объекта.  
  
 Объект визуальному элементу управления должен иметь его **DATASRC** параметру присвоить **RDS. DataControl**и его **DATAFLD** свойство значение **записей** объект поля (столбца).  
  
 В этом руководстве задайте **SourceRecordset** свойство:  
  
```vb
Sub RDSTutorial5()  
   Dim DS as New RDS.DataSpace  
   Dim RS as ADODB.Recordset  
   Dim DC as New RDS.DataControl  
   Dim DF as Object  
   Set DF = DS.CreateObject("RDSServer.DataFactory", "https://yourServer")  
   Set RS = DF.Query ("DSN=Pubs", "SELECT * FROM Authors")  
   DC.SourceRecordset = RS         ' Visual controls can now bind to DC.  
...  
```  
  
## <a name="see-also"></a>См. также  
 [Шаг 6. Изменения отправляются на сервер (учебник по RDS)](../../../ado/guide/remote-data-service/step-6-changes-are-sent-to-the-server-rds-tutorial.md)   
 [Учебник по RDS (VBScript)](../../../ado/guide/remote-data-service/rds-tutorial-vbscript.md)   
