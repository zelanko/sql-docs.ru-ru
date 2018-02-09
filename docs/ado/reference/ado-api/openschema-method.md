---
title: "Метод OpenSchema | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Connection15::OpenSchema
- Connection15::raw_OpenSchema
helpviewer_keywords:
- OpenSchema method [ADO]
ms.assetid: 850cf3ce-f18f-4e7c-8597-96c1dc504866
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf2b79bc39ff1f376801b5df6c24a768067a53b9
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="openschema-method"></a>Метод OpenSchema
Получает сведения о схеме базы данных от поставщика.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = connection.OpenSchema(QueryType, Criteria, SchemaID)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объект, содержащий сведения о схеме. **Записей** будет открыт как курсор только для чтения. *QueryType* определяет, какие столбцы должны отображаться в **записей**.  
  
#### <a name="parameters"></a>Параметры  
 *QueryType*  
 Любой [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) значение, представляющее тип схемы запроса для запуска.  
  
 *Условия*  
 Необязательно. Массив ограничений запросов для каждого *QueryType* параметра, как указано в [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md).  
  
 *SchemaID*  
 Идентификатор GUID схемы поставщика запросов, не определенных в спецификации OLE DB. Этот параметр является обязательным, если *QueryType* равно **adSchemaProviderSpecific**; в противном случае он не используется.  
  
## <a name="remarks"></a>Remarks  
 **OpenSchema** метод возвращает описательные сведения об источнике данных, например, таблицы в источнике данных столбцы в таблицах, и поддерживаемые типы данных.  
  
 *QueryType* аргумент имеет значение GUID, которое указывает, возвращаются столбцы (схемы). Спецификация OLE DB содержит полный список схем.  
  
 *Критерии* аргумент ограничивает результаты запроса схемы. *Критерии* задает массив значений, которые должны быть выполнены в соответствующий подмножество столбцов, называемых столбцами ограничение, в результате **записей**.  
  
 Константа **adSchemaProviderSpecific** используется для *QueryType* аргумент, если поставщик определяет собственный запросов нестандартное схемы за этими перечисленными выше. При использовании этой константы *SchemaID* аргумента требуется передать идентификатор GUID схемы запроса для выполнения. Если *QueryType* равно **adSchemaProviderSpecific** , но *SchemaID* не указан, будет выдана ошибка.  
  
 Поставщики не требуются для поддержки всех запросов стандартной схемы OLE DB. В частности только **adSchemaTables**, **adSchemaColumns**, и **adSchemaProviderTypes** требуются спецификации OLE DB. Однако поставщик не требуется для поддержки *критерии* ограничений, перечисленных выше для запросов этих схем.  
  
> [!NOTE]
>  **Удаленное использование службы данных** **OpenSchema** метод не доступен на стороне клиента [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
> [!NOTE]
>  В Visual Basic, столбцов, имеющих четырехбайтовое целое число без знака (DBTYPE UI4) **набора записей** , возвращенные **OpenSchema** метод **подключения** объекта не может сравнить с другими переменными. Дополнительные сведения о типах данных OLE DB см. в разделе [типов данных в OLE DB (OLE DB)](http://msdn.microsoft.com/en-us/6039292f-74e0-49b2-b133-17bc117ebf6a) и [типов данных в приложении A:](http://msdn.microsoft.com/en-us/e3a0533a-2196-4eb0-a31e-92fe9556ada6) в ссылке на Microsoft программиста OLE DB.  
  
> [!NOTE]
>  **Пользователи Visual C/C++** при не использует клиентские курсоры, получение «ORDINAL_POSITION» столбец схемы в ADO возвращает разновидностью VT_R8 MDAC 2.7, компоненты MDAC версии 2.8 и компоненты доступа к данным Windows (Windows DAC) 6.0, что типом, используемые в компонентах MDAC 2.6 был VT_I4. Программ, написанных для MDAC 2.6, только найдите вариант вернул типа VT_I4 будет получена ноль для каждого порядковый номер, если выполняются под MDAC 2.7, компоненты MDAC версии 2.8 и Windows DAC 6.0 без изменений. Это изменение было внесено, так как тип данных, который возвращает OLE DB является DBTYPE_UI4 и в тип со знаком VT_I4 не достаточно места для хранения всех возможных значений без возможно усечение происходит и тем самым вызывая потери данных.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода OpenSchema (Visual Basic)](../../../ado/reference/ado-api/openschema-method-example-vb.md)   
 [Пример метода OpenSchema (VC ++)](../../../ado/reference/ado-api/openschema-method-example-vc.md)   
 [Метод Open (соединение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (ADO запись)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Open (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
