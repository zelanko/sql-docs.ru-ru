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
ms.openlocfilehash: b2080145e00c658288f9d34e3fa42ed335e0c1d9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931866"
---
# <a name="openschema-method"></a>Метод OpenSchema
Получает сведения о схеме базы данных от поставщика.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = connection.OpenSchema(QueryType, Criteria, SchemaID)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает объект [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , содержащий сведения о схеме. **Набор записей** будет открыт как статический курсор только для чтения. *QueryType* определяет, какие столбцы отображаются в **наборе записей**.  
  
#### <a name="parameters"></a>Параметры  
 *QueryType*  
 Любое значение [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md) , представляющее тип выполняемого запроса схемы.  
  
 *Критерии*  
 Необязательный параметр. Массив ограничений запроса для каждого параметра *QueryType* , как указано в [SchemaEnum](../../../ado/reference/ado-api/schemaenum.md).  
  
 *счемаид*  
 Идентификатор GUID для запроса схемы поставщика, не определяемый спецификацией OLE DB. Этот параметр является обязательным, если для *QueryType* задано значение **адсчемапровидерспеЦифик**. в противном случае он не используется.  
  
## <a name="remarks"></a>Remarks  
 Метод **OpenSchema** возвращает собственные описательные сведения об источнике данных, например о таблицах, которые находятся в источнике данных, столбцах в таблицах и поддерживаемых типах данных.  
  
 Аргумент *QueryType* — это идентификатор GUID, который указывает, какие столбцы (схемы) возвращены. Спецификация OLE DB содержит полный список схем.  
  
 Аргумент *условия_отбора* ограничивает результаты запроса схемы. *Критерий* задает массив значений, которые должны находиться в соответствующем подмножестве столбцов, называемых столбцами ограничений, в результирующем **наборе записей**.  
  
 Константа **адсчемапровидерспеЦифик** используется для аргумента *QueryType* , если поставщик определяет собственные нестандартные запросы к схеме за пределами перечисленных выше. При использовании этой константы аргумент *счемаид* необходим для передачи идентификатора GUID выполняемого запроса схемы. Если *QueryType* имеет значение **АдсчемапровидерспеЦифик** , но *счемаид* не предоставлено, возникнет ошибка.  
  
 Поставщики не обязаны поддерживать все OLE DB запросы стандартной схемы. В частности, для спецификации OLE DB требуются только **адсчематаблес**, **адсчемаколумнс**и **адсчемапровидертипес** . Однако поставщик не обязан поддерживать ограничения *критерия* , перечисленные выше для этих запросов схемы.  
  
> [!NOTE]
>  **Использование удаленной службы данных** Метод **OpenSchema** недоступен для объекта [подключения](../../../ado/reference/ado-api/connection-object-ado.md) на стороне клиента.  
  
> [!NOTE]
>  В Visual Basic столбцы, имеющие 4-байтное целое число без знака (DBTYPE UI4) в **наборе записей** , возвращенном методом **OpenSchema** для объекта **соединения** , не могут сравниваться с другими переменными. Дополнительные сведения о типах данных OLE DB см. в разделе [типы данных в OLE DB (OLE DB)](https://msdn.microsoft.com/6039292f-74e0-49b2-b133-17bc117ebf6a) и [приложении A: типы данных](https://msdn.microsoft.com/e3a0533a-2196-4eb0-a31e-92fe9556ada6) в справочнике программиста Microsoft OLE DB.  
  
> [!NOTE]
>  **Пользователи Visual C/C++** Если не использовать курсоры на стороне клиента, получение "ORDINAL_POSITION" схемы столбца в ADO возвращает вариант типа VT_R8 в MDAC 2,7, MDAC 2,8 и компонентах доступа к данным Windows (Windows DAC) 6,0, а тип, используемый в MDAC 2,6, был VT_I4. Программы, написанные для MDAC 2,6, которые ищут только вариант, возвращаемый типом VT_I4, будут получать ноль для каждого порядкового номера, если они работают в MDAC 2,7, MDAC 2,8 и Windows DAC 6,0 без изменения. Это изменение произошло из-за того, что тип данных, OLE DB, возвращает DBTYPE_UI4, а в типе VT_I4 со знаком не хватает места для хранения всех возможных значений без необходимости усечения и, следовательно, причиной потери данных.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода OpenSchema (Visual Basic)](../../../ado/reference/ado-api/openschema-method-example-vb.md)   
 [Пример метода OpenSchema (Visual c++)](../../../ado/reference/ado-api/openschema-method-example-vc.md)   
 [Метод Open (подключение ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Метод Open (запись ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Метод Open (набор записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Метод Open (поток ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
