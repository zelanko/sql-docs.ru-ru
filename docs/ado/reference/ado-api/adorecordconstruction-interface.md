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
ms.openlocfilehash: 4dca796e9ba3c353d48fd3620c34a141c35a3fe8
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242834"
---
# <a name="adorecordconstruction-interface"></a>Интерфейс ADORecordConstruction
Интерфейс **адорекордконструктион**используется для создания объекта **записи** ADO из объекта **строки** OLE DB в приложении C/C++.  
  
 Этот интерфейс поддерживает следующие свойства:  
  
## <a name="properties"></a>Свойства  
  
|Свойство|Описание|  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Доступный только на запись.<br />Задает контейнер объекта OLE DB **строки** для этого объекта **записи** ADO.|  
|[Строка](../../../ado/reference/ado-api/row-property-ado.md)|Чтение и запись.<br />Возвращает или задает OLE DB объект **строки** от или в этом объекте ADO **Record** .|  
  
## <a name="methods"></a>Методы  
 Нет.  
  
## <a name="events"></a>События  
 Нет.  
  
## <a name="remarks"></a>Remarks  
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
  
 **Библиотека:** msado15.dll  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4
