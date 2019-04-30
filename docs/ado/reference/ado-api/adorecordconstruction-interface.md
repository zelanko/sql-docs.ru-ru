---
title: Интерфейс ADORecordConstruction | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction
helpviewer_keywords:
- ADORecordConstruction interface [ADO]
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21975fb2442aea97e362cd71b24c087f58addc0f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63248839"
---
# <a name="adorecordconstruction-interface"></a>Интерфейс ADORecordConstruction
**ADORecordConstruction**интерфейс используется для создания ADO **записи** объект из OLE DB **строки** объекта в приложении C/C++.  
  
 Этот интерфейс поддерживает следующие свойства:  
  
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Доступный только на запись.<br />Задает контейнер объекта OLE DB **строки** объект на этом ADO **записи** объекта.|  
|[строки](../../../ado/reference/ado-api/row-property-ado.md)|Чтение и запись.<br />Получает или задает поставщика OLE DB **строки** объект на этом ADO или из **записи** объекта.|  
  
## <a name="methods"></a>Методы  
 Нет.  
  
## <a name="events"></a>События  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 Учитывая OLE DB **строки** объекта (`pRow`), конструирование объекта ADO **записи** объекта (`adoR`), равносильно следующие три основные операции:  
  
1.  Создайте объект ADO **записи** объекта:  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  Запрос **IADORecordConstruction** интерфейс **записи** объекта:  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Вызовите **IADORecordConstruction::put_Row** метод свойство для задания OLE DB **строки** объекта ADO **записи** объекта:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 Полученный **adoR** теперь представляет объект ADO **записи** объект, созданный из OLE DB **строки** объекта.  
  
 ADO **записи** объект также может быть создан из контейнера OLE DB **строки** объекта.  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2.0 и более поздние версии  
  
 **Библиотека:** msado15.dll  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4
