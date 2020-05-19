---
title: Интерфейс Адостреамконструктион | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction
helpviewer_keywords:
- ADOStreamConstruction interface [ADO]
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
author: rothja
ms.author: jroth
ms.openlocfilehash: 2c120667a0ce279ea03922adf487f58c1fdc92de
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747057"
---
# <a name="adostreamconstruction-interface"></a>Интерфейс ADOStreamConstruction
Интерфейс **адостреамконструктион** используется для создания объекта **потока** ADO из OLE DB объекта **IStream** в приложении C/C++.  
  
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|[Свойство Stream](../../../ado/reference/ado-api/stream-property.md)|Чтение и запись. Возвращает или задает объект OLE DB **потока** .|  
  
## <a name="methods"></a>Методы  
 Нет.  
  
## <a name="events"></a>События  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 При наличии объекта OLE DB **IStream** ( `pStream` ) построение объекта **потока** ADO ( `adoStr` ) производится в следующие три основные операции:  
  
1.  Создайте объект **потока** ADO:  
  
    ```  
    Stream20Ptr adoStr;  
    adoStr.CreateInstance(__uuidof(Stream));  
    ```  
  
2.  Запросите интерфейс **иадостреамконструктион** в объекте **потока** :  
  
    ```  
    adoStreamConstructionPtr adoStrConstruct=NULL;  
    adoStr->QueryInterface(__uuidof(ADOStreamConstruction),  
                         (void**)&adoStrConstruct);  
    ```  
  
 Вызовите `IADOStreamConstruction::get_Stream` метод Property, чтобы задать OLE DB объект **IStream** в объекте **потока** ADO:  
  
```  
IUnknown *pUnk=NULL;  
pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
adoStrConstruct->put_Stream(pUnk);  
```  
  
 Результирующий `adoStr` объект теперь представляет объект **потока** ADO, созданный из OLE DB объекта **IStream** .  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2,0 или более поздняя версия  
  
 **Библиотека:** Msado15. dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)
