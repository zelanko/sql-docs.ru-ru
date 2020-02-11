---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aafcab3ad379dc25a2681a5d4f0d3f5e8d6eab5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67966673"
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
 Метод **CREATE** создает и открывает новое [соединение](../../../ado/reference/ado-api/connection-object-ado.md) ADO с источником данных, указанным в *ConnectString*. В случае успеха новый объект **Connection** назначается свойству [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) .  
  
 Если поставщик не поддерживает создание новых каталогов, возникнет ошибка.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример метода Create (Visual Basic)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Свойство ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
