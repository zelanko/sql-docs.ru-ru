---
title: Интерфейс ADORecordsetConstruction | Документы Microsoft
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
apitype: COM
f1_keywords:
- ADORecordsetConstruction
helpviewer_keywords:
- ADORecordsetConstruction interface [ADO]
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ff32133f7959b598d2c6bc7f2eb029906e66761
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Замечания  
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
