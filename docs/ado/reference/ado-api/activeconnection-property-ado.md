---
title: Свойство ActiveConnection (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::ActiveConnection
- Recordset15::get_ActiveConnection
- _Record::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO]
ms.assetid: 52d0a96c-14fb-4ad9-b004-4d821bc0a6db
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 951f43a2842162aa00f664dc83b754d06d8aafb2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684342"
---
# <a name="activeconnection-property-ado"></a>Свойство ActiveConnection (ADO)
Указывает, к которому [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта указанного [команда](../../../ado/reference/ado-api/command-object-ado.md), [записей](../../../ado/reference/ado-api/recordset-object-ado.md), или [записи](../../../ado/reference/ado-api/record-object-ado.md) в данный момент принадлежит объект.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, которое содержит определение для подключения, если подключение закрыто, или объект **Variant** содержащая текущие **подключения** объекта, если подключение открыто. Значение по умолчанию — пустая ссылка на объект. См. в разделе [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойство.  
  
## <a name="remarks"></a>Примечания  
 Используйте **ActiveConnection** свойства, чтобы определить **подключения** объекта, по которому указанного **команда** объекта будут выполняться или указанный  **Набор записей** будет открыт.  
  
## <a name="command"></a>Command  
 Для **команда** объектов, **ActiveConnection** свойство доступно для чтения/записи.  
  
 При попытке вызвать [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метод **команда** объекта до установки этого свойства открытый **подключения** объекта или допустимую строку соединения, происходит ошибка.  
  
 Если **подключения** присвоить объект **ActiveConnection** свойство, объект должен быть открыт. Назначение закрытого объекта соединения приводит к ошибке.  
  
### <a name="note"></a>Примечание  
 **Microsoft Visual Basic** параметр **ActiveConnection** свойства *ничего не* отменяет связь **команда** объекта из текущего **Подключения** и вызывает службу, чтобы освободить все связанные ресурсы в источнике данных. Затем можно связать **команда** объект с той же или другой **подключения** объекта. Некоторые поставщики позволяют изменять параметр свойства из одного **подключения** на другой без необходимости сначала задайте для свойства значение *ничего не*.  
  
 Если [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекцию **команда** объект содержит параметры, предоставленные поставщиком, коллекция очищается, если задать **ActiveConnection** свойства *ничего не* или в другой **подключения** объекта. Если вручную [параметр](../../../ado/reference/ado-api/parameter-object.md) объектов и использовать их для заполнения **параметры** коллекцию **команда** объекта, присвоив **ActiveConnection**  свойства *ничего не* или в другой **подключения** объект оставляет **параметры** коллекции без изменений.  
  
 Закрытие **подключения** объект, с которым **команда** объект имеет связанные наборы **ActiveConnection** свойства *ничего не*. Установка этого свойства в закрытом **подключения** возвращает ошибку.  
  
## <a name="recordset"></a>набор записей  
 Для открытой **записей** объектов или для **набор записей** объектов, [источника](../../../ado/reference/ado-api/source-property-ado-recordset.md) задано допустимое **команда** объект, **ActiveConnection** свойство доступно только для чтения. В противном случае — это чтение и запись.  
  
 Это свойство можно задать на допустимый **подключения** объекта или допустимую строку соединения. В этом случае создает новый поставщик **подключения** с помощью этого определения и открывает соединение. Кроме того, поставщик может присвоить этому свойству новый **подключения** объектов дают возможность доступа к **подключения** сведения об ошибке, или для выполнения других команд.  
  
 При использовании *ActiveConnection* аргумент [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод, чтобы открыть **записей** объекта, **ActiveConnection** будет свойство Наследовать значение аргумента.  
  
 Если задать **источника** свойство **записей** объекта на допустимый **команда** объектной переменной, **ActiveConnection** свойство **записей** наследует параметр **команда** объекта **ActiveConnection** свойство.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **записей** объект, это свойство можно задать только на строку подключения или (в Microsoft Visual Basic или Visual Basic Scripting Edition) *Nothing* .  
  
## <a name="record"></a>Записей  
 Это свойство доступно для чтения/записи при **записи** объект закрывается и может содержать строки подключения или ссылку на открытую **подключения** объекта. Это свойство только для чтения при **записи** объект открыт и содержит ссылку на открытую **подключения** объекта.  
  
 Объект **подключения** объекта создается неявно при **записи** объект открыт из URL-адрес. Откройте **записи** с существующим, откройте **подключения** объекта путем назначения **подключения** к этому свойству, или помощи **подключения** объект в качестве параметра в [откройте](../../../ado/reference/ado-api/open-method-ado-record.md) вызова метода. Если **записи** открывается из существующего **записи** или [набор записей](../../../ado/reference/ado-api/recordset-object-ado.md), а затем автоматически связывается с этим **записи** или  **Набор записей** объекта **подключения** объекта.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление свойства пример (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление пример свойства (Visual C++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление примеры свойств (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)
