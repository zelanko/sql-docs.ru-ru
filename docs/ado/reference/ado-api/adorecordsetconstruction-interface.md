---
title: Интерфейс Адорекордсетконструктион | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction
helpviewer_keywords:
- ADORecordsetConstruction interface [ADO]
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1e1d14255acd4cc7f18abea1c494353ef970903c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920797"
---
# <a name="adorecordsetconstruction-interface"></a>Интерфейс ADORecordsetConstruction
Интерфейс **адорекордсетконструктион** используется для создания объекта **набора записей** ADO из объекта OLE DB **набора строк** в приложении C/C++.  
  
 Этот интерфейс поддерживает следующие свойства:  
  
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|[Глава](../../../ado/reference/ado-api/chapter-property-ado.md)|Чтение и запись.<br />Получает или задает OLE DB объект **главы** от/в этом объекте ADO **Recordset** .|  
|[ровпоситион](../../../ado/reference/ado-api/rowposition-property-ado.md)|Чтение и запись.<br />Возвращает или задает OLE DB объект **ровпоситион** из или в этом объекте ADO **Recordset** .|  
|[Набор строк](../../../ado/reference/ado-api/rowset-property-ado.md)|Чтение и запись.<br />Возвращает или задает OLE DB объект **набора строк** из или в этом объекте ADO **Recordset** .|  
  
## <a name="methods"></a>Методы  
 Нет.  
  
## <a name="events"></a>События  
 Нет.  
  
## <a name="remarks"></a>Remarks  
 При наличии объекта **набора строк** OLE DB`pRowset`() построение объекта **набора записей** ADO (`adoRs`) производится в следующие три основные операции:  
  
1.  Создайте объект **набора записей** ADO.  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  Запросите интерфейс **иадорекордсетконструктион** в объекте **Recordset** :  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  Вызовите `IADORecordsetConstruction::put_Rowset` метод Property, чтобы задать объект `Rowset` OLE DB объекта ADO `Recordset` :  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 Результирующий `adoRs` объект теперь представляет объект ADO **Recordset** , созданный из объекта OLE DB **Rowset** .  
  
 Можно также создать объект **набора записей** ADO из OLE DB **главы** или объекта **ровпоситион** .  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2,0 и более поздние версии  
  
 **Библиотека:** Msado15. dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>См. также:  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Свойство Rowset (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)
