---
title: "Инструкция UPDATE MEMBER (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE_MEMBER
- UPDATE MEMBER
- MEMBER
- UPDATE
helpviewer_keywords:
- calculated members [MDX]
- UPDATE MEMBER statement
ms.assetid: 07ab708d-d165-4fb1-a9f9-fb8197ff0dab
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e126f34be1f1cecd1a793b71ff4b64069c1802c3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-definition---update-member"></a>Определение данных MDX - UPDATE MEMBER
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Обновляет существующий вычисляемый элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UPDATE MEMBER Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, содержащее имя куба, в котором находится элемент.  
  
 *Member_Name*  
 Допустимое строковое выражение, содержащее имя существующего элемента.  
  
 *MDX_Expression*  
 Допустимое многомерное выражение, в котором находится элемент, который должен быть обновлен.  
  
 *Property_name*  
 Допустимое строковое выражение, содержащее имя свойства вычисляемого элемента.  
  
 *Property_Value*  
 Допустимое скалярное выражение, содержащее значение свойства вычисляемого элемента.  
  
## <a name="remarks"></a>Remarks  
 Инструкция UPDATE MEMBER обновляет существующие вычисляемые элементы, сохраняя относительную очередность элемента по отношению к другим вычислениям. Поэтому использовать инструкцию UPDATE MEMBER для изменения элемента SOLVEORDER нельзя.  
  
 Инструкцию UPDATE MEMBER нельзя указать в скрипте многомерных выражений для куба.  
  
 При указании куба, отличного от текущего подключенного куба, возникает ошибка. Поэтому для обращения к текущему кубу вместо указания имени куба рекомендуется использовать переменную CURRENTCUBE.  
  
 Дополнительные сведения о свойствах элементов, определенных в OLE DB, см. в документации OLE DB.  
  
## <a name="standard-properties"></a>Стандартные свойства  
 У каждого элемента есть набор стандартных свойств. В следующей таблице перечислены эти стандартные свойства.  
  
|Идентификатор свойства|Значение|  
|-------------------------|-------------|  
|FORMAT_STRING|Объект [!INCLUDE[msCoName](../includes/msconame-md.md)] строка форматирования Office, клиентское приложение можно использовать для отображения значений ячеек.|  
|VISIBLE|Значение, определяющее видимость вычисляемого элемента в наборе строк схемы. Видимые вычисляемые элементы могут добавляться к набору функцией [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) функции. Ненулевое значение указывает, что данный вычисляемый элемент видим. Значение по умолчанию для этого свойства — *Visible*.<br /><br /> Невидимые вычисляемые элементы обычно используются как промежуточные шаги при вычислении более сложных элементов. К таким вычисляемым элементам могут также обращаться другие типы элементов, например меры.|  
|NON_EMPTY_BEHAVIOR|Мера или набор, используемые для определения поведения вычисляемых элементов при разрешении пустых ячеек.|  
|CAPTION|Значение строки, определяющее заголовок, используемый клиентским приложением для отображения элемента.|  
|DISPLAY_FOLDER|Значение строки, указывающее путь к папке отображения, в которой элемент будет отображаться клиентским приложением. Разделитель уровней вложенности папок определяется клиентским приложением. Для средств и клиентов, входящих в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], обратная косая черта (\\) в качестве разделителя уровней. Чтобы указать для определенного элемента несколько папок отображения, используйте точку с запятой (;) для разделения папок.|  
|ASSOCIATED_MEASURE_GROUP|Имя группы мер, с которой связан элемент.|  
  
## <a name="see-also"></a>См. также:  
 [Инструкция DROP MEMBER &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-drop-member.md)   
 [CREATE MEMBER, инструкция #40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-create-member.md)   
 [Инструкции определения данных &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
