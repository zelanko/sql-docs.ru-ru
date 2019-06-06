---
title: Основные принципы ADOX | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADOX, fundamentals
ms.assetid: 954476fc-5f72-4ada-ace5-d9acb27d18f8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 824c3fd5121aca7638d67cc3606d8280f75e255b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66699677"
---
# <a name="adox-fundamentals"></a>Основные принципы ADOX
Модули Microsoft® ActiveX® Data объекты для языка описания данных и безопасности (ADOX) — это расширение объектов ADO и модель программирования. ADOX содержит объекты для создания схем и изменения, а также безопасности. Поскольку это объектно ориентированный подход для операций со схемой, можно написать код, который будет работать для различных данных источников независимо от различий в их собственном вариантов синтаксиса.  
  
 ADOX — это вспомогательная Библиотека базовых объектов ADO. Он предоставляет дополнительные объекты для создание, изменение и удаление объектов схемы, например таблицы и процедуры. Она также включает объекты безопасности для обслуживания пользователей и групп, а также для предоставления или отмены разрешения на объекты.  
  
 Чтобы использовать ADOX со средством разработки, необходимо установить ссылку на библиотеку типов ADOX. Описание библиотеки ADOX — «Microsoft ADO Ext. DDL и безопасности.» Имя файла библиотеки ADOX Msadox.dll, и код программы (ProgID) — «ADOX». Дополнительные сведения о задании ссылки на библиотеки см. в документации средства разработки.  
  
 Поставщик Microsoft OLE DB для ядра СУБД Microsoft Jet полностью поддерживает ADOX. Некоторые возможности ADOX могут не поддерживаться, в зависимости от поставщика данных.  
  
 В этом документе предполагает практический опыт Microsoft® Visual Basic®, языка программирования и общие знания ADO. Дополнительные сведения о ADO см. в разделе [руководство по программированию объектов ADO](../../../ado/guide/ado-programmer-s-guide.md). Дополнительные общие сведения о ADOX см. в разделах:  
  
-   [Объектная модель ADOX](../../../ado/reference/adox-api/adox-object-model.md)  
  
-   [Объекты ADOX](../../../ado/reference/adox-api/adox-objects.md)  
  
-   [Коллекции ADOX](../../../ado/reference/adox-api/adox-collections.md)  
  
-   [Свойства ADOX](../../../ado/reference/adox-api/adox-properties.md)  
  
-   [Методы ADOX](../../../ado/reference/adox-api/adox-methods.md)  
  
-   [Примеры ADOX](../../../ado/reference/adox-api/adox-code-examples.md)  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADOX](../../../ado/reference/adox-api/adox-api-reference.md)   
 [Примеры кода ADOX](../../../ado/reference/adox-api/adox-code-examples.md)   
 [Коллекции ADOX](../../../ado/reference/adox-api/adox-collections.md)   
 [Перечисляемые константы ADOX](../../../ado/reference/adox-api/adox-enumerated-constants.md)   
 [Методы ADOX](../../../ado/reference/adox-api/adox-methods.md)   
 [Объектная модель ADOX](../../../ado/reference/adox-api/adox-object-model.md)   
 [Объекты ADOX](../../../ado/reference/adox-api/adox-objects.md)   
 [Свойства ADOX](../../../ado/reference/adox-api/adox-properties.md)   
 [ADO (многомерные данные) (многомерные Объекты ADO)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Руководство по программированию объектов ADO](../../../ado/guide/ado-programmer-s-guide.md)
