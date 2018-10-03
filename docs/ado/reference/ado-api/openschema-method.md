---
title: Метод OpenSchema | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::OpenSchema
- Connection15::raw_OpenSchema
helpviewer_keywords:
- OpenSchema method [ADO]
ms.assetid: 850cf3ce-f18f-4e7c-8597-96c1dc504866
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3481d9b7c186f3492e403b6881f4ffafbe90912b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47787289"
---
# <a name="openschema-method"></a>Метод OpenSchema
Получает сведения о схеме базы данных от поставщика.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = connection.OpenSchema(QueryType, Criteria, SchemaID)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [записей](../../../ado/reference/ado-api/recordset-object-ado.md) , содержащий сведения о схеме. **Записей** будет открыт как курсор статичным, доступным только для чтения. *QueryType* определяет, какие столбцы должны отображаться в **записей**.  
  
#### <a name="parameters"></a>Параметры  
 *QueryType*  
 Любой [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) значение, представляющее тип запроса схемы для запуска.  
  
 *Критерии*  
 Необязательный параметр. Массив ограничений запросов для каждого *QueryType* параметра, как указано в [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md).  
  
 *SchemaID*  
 Идентификатор GUID для запроса схемы поставщика, не определенных в спецификации OLE DB. Этот параметр является обязательным, если *QueryType* присваивается **adSchemaProviderSpecific**; в противном случае он не используется.  
  
## <a name="remarks"></a>Примечания  
 **OpenSchema** метод возвращает описательные сведения об источнике данных, например, таблицы в источнике данных, столбцы в таблицах, и поддерживаемые типы данных.  
  
 *QueryType* аргумент представляет собой идентификатор GUID, который указывает, возвращаются столбцы (схемы). В спецификации OLE DB имеет полный список схем.  
  
 *Критерии* аргумент ограничивает результаты запроса схемы. *Критерии* указывает массив значений, которые должны произойти в соответствующий подмножество столбцов, называемых столбцами ограничение, в результате **записей**.  
  
 Константа **adSchemaProviderSpecific** используется для *QueryType* аргумент, если поставщик определяет свои собственные нестандартные схемы запросов за этими перечисленных выше. При использовании этой константы *SchemaID* аргумент необходимо передать идентификатор GUID запроса схемы для выполнения. Если *QueryType* присваивается **adSchemaProviderSpecific** , но *SchemaID* не указан, будет выдана ошибка.  
  
 Поставщики не требуются для поддержки всех запросов стандартной схемы OLE DB. В частности только **adSchemaTables**, **adSchemaColumns**, и **adSchemaProviderTypes** необходимы в спецификации OLE DB. Однако поставщик не требуется для поддержки *критерии* ограничений, перечисленных выше для этих запросов схемы.  
  
> [!NOTE]
>  **Удаленное использование службы данных** **OpenSchema** метод недоступен на стороне клиента [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
> [!NOTE]
>  В Visual Basic, столбцами, имеющими целого числа без знака размером 4 байта (DBTYPE UI4) во **набор записей** возвращаемые **OpenSchema** метод **подключения** объект нельзя похож на другие переменные. Дополнительные сведения о типах данных OLE DB см. в разделе [типы данных в OLE DB (OLE DB)](http://msdn.microsoft.com/6039292f-74e0-49b2-b133-17bc117ebf6a) и [типы данных о приложении](http://msdn.microsoft.com/e3a0533a-2196-4eb0-a31e-92fe9556ada6) справочника Microsoft программиста OLE DB.  
  
> [!NOTE]
>  **Пользователи Visual C/C++** без использования курсоров на стороне клиента, извлечение «ORDINAL_POSITION» столбец схемы в ADO возвращает разновидностью VT_R8 MDAC 2.7, MDAC 2.8 и компоненты доступа к данным Windows (Windows DAC) 6.0, а тип, используемый в состав компонентов MDAC 2.6 было VT_I4. Программы, написанные для компонентов MDAC 2.6 подобное только для типа variant вернул типа VT_I4 получит в нулевое значение для каждого порядковый номер, если выполняются под MDAC 2.7, MDAC 2.8 и 6.0 Windows приложения уровня данных без изменений. Это изменение было внесено, так как тип данных, OLE DB возвращает DBTYPE_UI4, а в тип со знаком VT_I4 не хватает места для хранения всех возможных значений без возможно усечение происходит и тем самым приводит к потере данных.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода OpenSchema (Visual Basic)](../../../ado/reference/ado-api/openschema-method-example-vb.md)   
 [Пример метода OpenSchema (Visual C++)](../../../ado/reference/ado-api/openschema-method-example-vc.md)   
 [Метод Open (объект Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (объект Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Open (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
