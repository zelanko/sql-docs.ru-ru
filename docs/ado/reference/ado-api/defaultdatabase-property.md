---
title: Свойство DefaultDatabase | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: 2b7fc72d99273428a1ab4a11f12a021079d8faac
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277463"
---
# <a name="defaultdatabase-property"></a>Свойство DefaultDatabase
Указывает базу данных по умолчанию для [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, представляющее имя базы данных от поставщика.  
  
## <a name="remarks"></a>Примечания  
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
