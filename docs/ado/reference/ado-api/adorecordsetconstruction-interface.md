---
title: Интерфейс ADORecordsetConstruction | Документация Майкрософт
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920797"
---
# <a name="adorecordsetconstruction-interface"></a>Интерфейс ADORecordsetConstruction
**ADORecordsetConstruction** интерфейс используется для создания ADO **записей** объект из OLE DB **набора строк** объекта в приложении C/C++.  
  
 Этот интерфейс поддерживает следующие свойства:  
  
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|[Глава](../../../ado/reference/ado-api/chapter-property-ado.md)|Чтение и запись.<br />Получает или задает поставщика OLE DB **глава** объект на этом ADO или из **записей** объекта.|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|Чтение и запись.<br />Получает или задает поставщика OLE DB **RowPosition** объект на этом ADO или из **записей** объекта.|  
|[Функции набора строк](../../../ado/reference/ado-api/rowset-property-ado.md)|Чтение и запись.<br />Получает или задает поставщика OLE DB **набора строк** объект на этом ADO или из **записей** объекта.|  
  
## <a name="methods"></a>Методы  
 Нет.  
  
## <a name="events"></a>События  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 Учитывая OLE DB **набора строк** объекта (`pRowset`), конструирование объекта ADO **записей** объекта (`adoRs`) равносильно следующие три основные операции:  
  
1.  Создайте объект ADO **записей** объекта:  
  
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
  
3.  Вызовите `IADORecordsetConstruction::put_Rowset` метод свойство для задания OLE DB `Rowset` объекта ADO `Recordset` объекта:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 Полученный `adoRs` теперь представляет объект ADO **записей** объект, созданный из OLE DB **набора строк** объекта.  
  
 Можно также создать объект ADO **записей** объект из OLE DB **глава** или **RowPosition** объекта.  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2.0 и более поздние версии  
  
 **Библиотека:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>См. также  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Свойство Rowset (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)
