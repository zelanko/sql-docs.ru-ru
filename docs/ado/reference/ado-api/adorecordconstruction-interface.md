---
title: Интерфейс Адорекордконструктион | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 12a9b2cae1c516ed3bf8caef8127034e6ff2a847
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82747176"
---
# <a name="adorecordconstruction-interface"></a>Интерфейс ADORecordConstruction
Интерфейс **адорекордконструктион**используется для создания объекта **записи** ADO из объекта **строки** OLE DB в приложении C/C++.  
  
 Этот интерфейс поддерживает следующие свойства:  
  
## <a name="properties"></a>Свойства  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Доступный только на запись.<br />Задает контейнер объекта OLE DB **строки** для этого объекта **записи** ADO.|  
|[Строки](../../../ado/reference/ado-api/row-property-ado.md)|Чтение и запись.<br />Возвращает или задает OLE DB объект **строки** от или в этом объекте ADO **Record** .|  
  
## <a name="methods"></a>Методы  
 Нет.  
  
## <a name="events"></a>События  
 Нет.  
  
## <a name="remarks"></a>Примечания  
 При наличии объекта **строки** OLE DB ( `pRow` ) построение объекта **записи** ADO () производится в `adoR` следующие три основные операции:  
  
1.  Создайте объект **записи** ADO.  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  Запросите интерфейс **иадорекордконструктион** в объекте **Record** :  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Вызовите метод свойства **иадорекордконструктион::p ut_Row** , чтобы задать объект **строки** OLE DB в объекте **записи** ADO:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 Результирующий объект **Адор** теперь представляет объект **записи** ADO, созданный из объекта **строки** OLE DB.  
  
 Объект **записи** ADO также может быть создан из контейнера объекта **строки** OLE DB.  
  
## <a name="requirements"></a>Требования  
 **Версия:** ADO 2,0 и более поздние версии  
  
 **Библиотека:** Msado15. dll  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4
