---
description: Основные принципы ADOX
title: Основы ADOX | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADOX, fundamentals
ms.assetid: 954476fc-5f72-4ada-ace5-d9acb27d18f8
author: rothja
ms.author: jroth
ms.openlocfilehash: d24e7a61642ed9945dfc69a06c584b2423775659
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978705"
---
# <a name="adox-fundamentals"></a>Основные принципы ADOX
Microsoft® ActiveX® расширения объектов данных для языка описания данных и системы безопасности (ADOX) — это расширение объектов ADO и модели программирования. ADOX включает объекты для создания и изменения схем, а также для обеспечения безопасности. Поскольку это основанный на объектах подход к обработке схем, можно написать код, который будет работать с различными источниками данных независимо от различий в их синтаксисе.  
  
 ADOX — это вспомогательная библиотека для основных объектов ADO. Он предоставляет дополнительные объекты для создания, изменения и удаления объектов схемы, таких как таблицы и процедуры. Он также включает объекты безопасности для обслуживания пользователей и групп и предоставления и отзыва разрешений на объекты.  
  
 Чтобы использовать ADOX с вашим средством разработки, необходимо установить ссылку на библиотеку типов ADOX. Описание библиотеки ADOX: «Microsoft ADO ext. for DDL and Security». Имя файла библиотеки ADOX — Msadox.dll, идентификатор программы (ProgID) — "ADOX". Дополнительные сведения об установке ссылок на библиотеки см. в документации по средству разработки.  
  
 Поставщик Microsoft OLE DB для Microsoft Jet ядро СУБД полностью поддерживает ADOX. Некоторые функции ADOX могут не поддерживаться в зависимости от поставщика данных.  
  
 В этом документе предполагается, что опыт работы с языком программирования Microsoft® Visual Basic® и общие знания ADO. Дополнительные сведения об ADO см. в документации [по программисту ADO](../ado-programmer-s-guide.md). Дополнительные сведения о ADOX см. в следующих разделах:  
  
-   [Объектная модель ADOX](../../reference/adox-api/adox-object-model.md)  
  
-   [Объекты ADOX](../../reference/adox-api/adox-objects.md)  
  
-   [Коллекции ADOX](../../reference/adox-api/adox-collections.md)  
  
-   [Свойства ADOX](../../reference/adox-api/adox-properties.md)  
  
-   [Методы ADOX](../../reference/adox-api/adox-methods.md)  
  
-   [Примеры ADOX](../../reference/adox-api/adox-code-examples.md)  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADOX](../../reference/adox-api/adox-object-model.md?view=sql-server-ver15)   
 [Примеры кода ADOX](../../reference/adox-api/adox-code-examples.md)   
 [ADOX коллекции](../../reference/adox-api/adox-collections.md)   
 [ADOX перечислимые константы](../../reference/adox-api/adox-enumerated-constants.md)   
 [Методы ADOX](../../reference/adox-api/adox-methods.md)   
 [Объектная модель ADOX](../../reference/adox-api/adox-object-model.md)   
 [Объекты ADOX](../../reference/adox-api/adox-objects.md)   
 [Свойства ADOX](../../reference/adox-api/adox-properties.md)   
 [ADO (многомерные) (объекты данных ActiveX (MD))](../multidimensional/ado-multidimensional-ado-md.md)   
 [Руководство по программированию объектов ADO](../ado-programmer-s-guide.md)