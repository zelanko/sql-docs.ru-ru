---
title: Интерфейс ADOStreamConstruction | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf21be88854837ab2dff1a8bc8bc73f44a6e20c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828752"
---
# <a name="adostreamconstruction-interface"></a>Интерфейс ADOStreamConstruction
**ADOStreamConstruction** интерфейс используется для создания ADO **Stream** объект из OLE DB **IStream** объекта в приложении C/C++.  
  
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|[Свойство Stream](../../../ado/reference/ado-api/stream-property.md)|Чтение и запись. Получает или задает поставщика OLE DB **Stream** объекта.|  
  
## <a name="methods"></a>Методы  
 Нет.  
  
## <a name="events"></a>События  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 Учитывая OLE DB **IStream** объекта (`pStream`), конструирование объекта ADO **Stream** объекта (`adoStr`) равносильно следующие три основные операции:  
  
1.  Создайте объект ADO **Stream** объекта:  
  
    ```  
    Stream20Ptr adoStr;  
    adoStr.CreateInstance(__uuidof(Stream));  
    ```  
  
2.  Запрос **IADOStreamConstruction** интерфейс **Stream** объекта:  
  
    ```  
    adoStreamConstructionPtr adoStrConstruct=NULL;  
    adoStr->QueryInterface(__uuidof(ADOStreamConstruction),  
                         (void**)&adoStrConstruct);  
    ```  
  
 Вызовите `IADOStreamConstruction::get_Stream` метод свойство для задания OLE DB **IStream** объекта ADO **Stream** объекта:  
  
```  
IUnknown *pUnk=NULL;  
pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
adoStrConstruct->put_Stream(pUnk);  
```  
  
 Полученный `adoStr` теперь представляет объект ADO **Stream** объект, созданный из OLE DB **IStream** объекта.  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2.0 или более поздней версии  
  
 **Библиотека:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](../../../ado/reference/ado-api/ado-api-reference.md)
