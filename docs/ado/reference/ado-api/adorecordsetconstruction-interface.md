---
title: "Интерфейс ADORecordsetConstruction | Документы Microsoft"
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
- ADORecordsetConstruction
helpviewer_keywords:
- ADORecordsetConstruction interface [ADO]
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: be4c36c5bd69fe6657b57d74e8808259fe602db0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="adorecordsetconstruction-interface"></a>Интерфейс ADORecordsetConstruction
**ADORecordsetConstruction** интерфейса используется для создания объекта ADO **записей** объектов из поставщика OLE DB **строк** объекта в приложении C/C++.  
  
 Этот интерфейс поддерживает следующие свойства:  
  
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|[Глава](../../../ado/reference/ado-api/chapter-property-ado.md)|Чтение и запись.<br />Получает или задает поставщика OLE DB **главе** объекта из/в этом ADO **записей** объекта.|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|Чтение и запись.<br />Получает или задает поставщика OLE DB **RowPosition** объекта из/в этом ADO **записей** объекта.|  
|[Функции набора строк](../../../ado/reference/ado-api/rowset-property-ado.md)|Чтение и запись.<br />Получает или задает поставщика OLE DB **строк** объекта из/в этом ADO **записей** объекта.|  
  
## <a name="methods"></a>Методы  
 Нет.  
  
## <a name="events"></a>События  
 Нет.  
  
## <a name="remarks"></a>Remarks  
 Получает OLE DB **набора строк** объекта (`pRowset`), построении ADO **набора записей** объекта (`adoRs`) суммы следующие три основные операции:  
  
1.  Создание объекта ADO **записей** объекта:  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  Запрос **IADORecordsetConstruction** интерфейс **записей** объекта:  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  Вызовите `IADORecordsetConstruction::put_Rowset` метод свойство, чтобы задать OLE DB `Rowset` объекта ADO `Recordset` объекта:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 Итоговые `adoRs` теперь представляет объект ADO **записей** объекта, построенным на основе OLE DB **строк** объекта.  
  
 Можно также создать ADO **записей** объектов из поставщика OLE DB **главе** или **RowPosition** объекта.  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2.0 и более поздних версий  
  
 **Библиотека:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>См. также  
 [Объект набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Свойство Rowset (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)
