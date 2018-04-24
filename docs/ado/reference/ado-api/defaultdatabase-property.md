---
title: Свойство DefaultDatabase | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f90b450fa2421d47a16946b20fdc707cc266b3e6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="defaultdatabase-property"></a>Свойство DefaultDatabase
Указывает базу данных по умолчанию для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, представляющее имя базы данных от поставщика.  
  
## <a name="remarks"></a>Замечания  
 Используйте **DefaultDatabase** свойство задает или возвращает имя базы данных по умолчанию на определенной **подключения** объекта.  
  
 Если база данных по умолчанию, строки SQL использовать неполное синтаксис для доступа к объектам базы данных. Для доступа к объектам в базе данных, отличной от той, указанный в **DefaultDatabase** свойства, необходимо полностью указывать имена объектов имя нужной базы данных. После создания соединения, поставщик будет записывать сведения о базе данных по умолчанию для **DefaultDatabase** свойство. Некоторые поставщики разрешают использовать только одну базу данных на один сеанс, в этом случае нельзя изменить **DefaultDatabase** свойство.  
  
 Некоторые источники данных и поставщики могут не поддерживать этот компонент и может вернуть ошибку или пустой строкой.  
  
> [!NOTE]
>  **Удаленное использование службы данных** это свойство доступно не на стороне клиента **подключения** объекта.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Поставщик и пример использования свойств DefaultDatabase (Visual Basic)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Примеры свойств Provider и DefaultDatabase (Visual C++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
