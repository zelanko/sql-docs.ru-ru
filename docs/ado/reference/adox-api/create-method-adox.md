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
manager: jroth
ms.openlocfilehash: bbdd7f6b663fb1c6c2ee12b7a6e4c843eb16d42d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703352"
---
# <a name="create-method-adox"></a>Метод Create (ADOX)
Создает новый каталог.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Catalog.Create ConnectString  
```  
  
#### <a name="parameters"></a>Параметры  
 *ConnectString*  
 Объект **строка** значение, используемое для подключения к источнику данных.  
  
## <a name="remarks"></a>Примечания  
 **Создать** метод создает и открывает новый ADO [подключения](../../../ado/reference/ado-api/connection-object-ado.md) к источнику данных, указанной в *ConnectString*. В случае успешного выполнения новый **подключения** присвоить объект [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) свойство.  
  
 Если поставщик не поддерживает создание новых каталогов, произойдет ошибка.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>См. также  
 [Создайте пример метода (Visual Basic)](../../../ado/reference/adox-api/create-method-example-vb.md)   
 [Свойство ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)
