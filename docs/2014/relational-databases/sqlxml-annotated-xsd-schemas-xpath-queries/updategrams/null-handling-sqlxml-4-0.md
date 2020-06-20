---
title: Обработка значений NULL (SQLXML 4,0) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 430643e8a6c9bd3dd00b2763990645c6a162ee40
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047492"
---
# <a name="null-handling-sqlxml-40"></a>Обработка значений NULL (SQLXML 4.0)
  Синтаксис XML определяет значение NULL как отсутствие. (Например, если атрибут или элемент имеет значение NULL, этот атрибут или элемент отсутствует в XML-документе.) В [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML `updg:nullvalue` атрибут позволяет указать значение NULL для элемента или значения атрибута.  
  
 Например, следующий диаграмма обновления гарантирует, что значение **заголовка** контакта со значением **ContactID** , равным 64, будет равно null, а затем обновите значение **заголовка** на «Mr». для этого контакта.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Когда параметры передаются диаграмме обновления, значение NULL может передаваться как значение параметра. Это осуществляется путем указания атрибута `nullvalue` в блоке `<updg:header>`. Пример см. в разделе [Передача параметров в диаграмм обновления &#40;SQLXML 4,0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>См. также:  
 [Вопросы безопасности диаграмма обновления &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
