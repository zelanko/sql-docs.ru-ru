---
description: Метод Create (ADOX)
title: Метод Create (ADOX) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_Create
- _Catalog::Create
helpviewer_keywords:
- Create method [ADOX]
ms.assetid: 64f5c21c-b581-42d8-bdc7-c4f1bebaf105
author: rothja
ms.author: jroth
ms.openlocfilehash: b5add8972d95413841a6c9c45de2dcc26d8cbb24
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770843"
---
# <a name="create-method-adox"></a>Метод Create (ADOX)
Создает новый каталог.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Параметры  
 *ConnectString*  
 **Строковое** значение, используемое для подключения к источнику данных.  
  
## <a name="remarks"></a>Remarks  
 Метод **CREATE** создает и открывает новое [соединение](../ado-api/connection-object-ado.md) ADO с источником данных, указанным в *ConnectString*. В случае успеха новый объект **Connection** назначается свойству [ActiveConnection](./activeconnection-property-adox.md) .  
  
 Если поставщик не поддерживает создание новых каталогов, возникнет ошибка.  
  
## <a name="applies-to"></a>Применение  
 [Объект Catalog (ADOX)](./catalog-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Пример метода Create (Visual Basic)](./create-method-example-vb.md)   
 [Свойство ActiveConnection (ADOX)](./activeconnection-property-adox.md)