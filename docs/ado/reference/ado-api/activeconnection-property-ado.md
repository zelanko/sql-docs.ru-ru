---
title: "Свойство ActiveConnection (ADO) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Command15::ActiveConnection
- Recordset15::get_ActiveConnection
- _Record::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO]
ms.assetid: 52d0a96c-14fb-4ad9-b004-4d821bc0a6db
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 431438fa61750ca2f8eaee3362f94188e5985523
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="activeconnection-property-ado"></a>Свойство ActiveConnection (ADO)
Указывает, к которому [подключения](../../../ado/reference/ado-api/connection-object-ado.md) указанного объекта [команда](../../../ado/reference/ado-api/command-object-ado.md), [записей](../../../ado/reference/ado-api/recordset-object-ado.md), или [записи](../../../ado/reference/ado-api/record-object-ado.md) принадлежит объект.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, которое содержит определение для подключения, если подключение закрыто, или **Variant** содержащая текущие **подключения** объекта, если соединение будет открыт. Значение по умолчанию — пустая ссылка на объект. В разделе [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойство.  
  
## <a name="remarks"></a>Замечания  
 Используйте **ActiveConnection** свойства, чтобы определить **подключения** объекта, для которого указанный **команда** объект будет выполняться или только указанные  **Набор записей** будет открыт.  
  
## <a name="command"></a>Command  
 Для **команда** объектов, **ActiveConnection** свойство доступно для чтения/записи.  
  
 При попытке вызвать [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) метод **команда** объекта до этого свойства открытый **подключения** объекта или допустимую строку соединения, происходит ошибка.  
  
 Если **подключения** объект присваивается **ActiveConnection** свойства, объект должен быть открыт. Назначение закрытый объект соединения приводит к ошибке.  
  
### <a name="note"></a>Примечание  
 **Microsoft Visual Basic** параметр **ActiveConnection** свойства *ничего* отсоединяет **команда** объекта из текущего **Подключения** и вызывает службу, чтобы освободить все связанные ресурсы в источнике данных. Затем можно связать **команда** объект с тем же или другой **подключения** объекта. Некоторые поставщики разрешают использовать для изменения значения свойства из одного **подключения** на другой, без необходимости сначала присвойте свойству *ничего не*.  
  
 Если [параметры](../../../ado/reference/ado-api/parameters-collection-ado.md) коллекцию **команда** объект содержит параметры, предоставленные поставщиком, коллекция очищается при установке **ActiveConnection** свойства *ничего* или другим **подключения** объекта. Если вручную создать [параметр](../../../ado/reference/ado-api/parameter-object.md) объекты и использовать их для заполнения **параметры** коллекцию **команда** объекта, присвоив **ActiveConnection**  свойства *ничего* или другим **подключения** объект оставляет **параметры** коллекции без изменений.  
  
 Закрытие **подключения** объекта, с которым **команда** объектов — связанные наборы **ActiveConnection** свойства *ничего не*. Установка этого свойства в закрытый **подключения** возвращает ошибку.  
  
## <a name="recordset"></a>набор записей  
 Для открытия **записей** объектов или для **записей** объектов, [источника](../../../ado/reference/ado-api/source-property-ado-recordset.md) задано допустимое **команды** объект, **ActiveConnection** свойство доступно только для чтения. В противном случае — это чтение и запись.  
  
 Это свойство можно задать допустимое **подключения** объекта или допустимую строку соединения. В этом случае поставщик создает новую **подключение** с помощью данного определения и открывает соединение. Кроме того, поставщик может установить это свойство к новому **подключения** объекта, чтобы получить возможность доступа к **подключения** объекта для расширенных сведений об ошибках или выполнять другие команды.  
  
 При использовании *ActiveConnection* аргумент [откройте](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод, чтобы открыть **записей** объекта, **ActiveConnection** свойство наследовать значения аргумента.  
  
 Если задать **источника** свойство **набора записей** объект является допустимым **команда** объектной переменной **ActiveConnection** свойство **записей** наследует параметр по **команда** объекта **ActiveConnection** свойство.  
  
> [!NOTE]
>  **Удаленное использование службы данных** при использовании на стороне клиента **записей** объекта, это свойство можно задать только на строку подключения или (в Microsoft Visual Basic или Visual Basic Scripting Edition) *Nothing* .  
  
## <a name="record"></a>Записей  
 Это свойство доступно для чтения/записи при **запись** объект закрывается и может содержать строку соединения или ссылку на открытый **подключения** объекта. Это свойство доступно только для чтения при **запись** объект открыт, а также содержит ссылку на открытый **подключения** объекта.  
  
 Объект **подключения** объекта создается неявно при **записи** открыть объект с URL-адреса. Откройте **запись** с существующим, откройте **подключения** объекта путем назначения **подключения** объект для этого свойства или с помощью **подключения** объект в качестве параметра в [откройте](../../../ado/reference/ado-api/open-method-ado-record.md) вызова метода. Если **запись** открывается из существующего **запись** или [записей](../../../ado/reference/ado-api/recordset-object-ado.md), автоматически связывается с, а затем **записи** или  **Набор записей** объекта **подключения** объекта.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
  
||||  
|-|-|-|  
|[Объект команды (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Объект записи (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>См. также:  
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection CommandText, CommandTimeout, CommandType, размер и направление примере свойства (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление-пример свойства (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)

