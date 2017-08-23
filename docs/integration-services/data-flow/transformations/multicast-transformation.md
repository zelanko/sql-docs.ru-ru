---
title: "Преобразование многоадресной рассылки | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.multicasttrans.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8619a0ed02ffc73126eb151f4a83a0b6b24c4be8
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="multicast-transformation"></a>преобразование «Многоадресная доставка»
  Преобразование «Многоадресная доставка» распределяет данные на входе на один или более выходов. Это преобразование схоже с преобразованием «Условное разбиение». Оба вида преобразований направляют данные на входе на несколько выходов. Их различие состоит в том, что преобразование «Многоадресная доставка» направляет каждую строку на все выходы, а преобразование «Условное разбиение» направляет одну строку на один выход. Дополнительные сведения см. в статье [Conditional Split Transformation](../../../integration-services/data-flow/transformations/conditional-split-transformation.md).  
  
 Можно производить настройку преобразования «Многоадресная доставка» путем добавления выходов.  
  
 Используя преобразование «Многоадресная доставка», пакет может создавать логические копии данных. Эта возможность полезна, если пакету необходимо применить несколько наборов преобразований к одним и тем же данным. Например, одна копия данных статистически обрабатывается и в назначение загружается только сводная информация, а в другую копию данных перед загрузкой в назначение добавляются значения уточняющего запроса и производные столбцы.  
  
 Это преобразование имеет один вход и несколько выходов. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-multicast-transformation"></a>Настройка преобразования «Многоадресная доставка»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Сведения о свойствах, которые можно установить в диалоговом окне **Редактор преобразования «Многоадресная доставка»** , см. в разделе [Multicast Transformation Editor](../../../integration-services/data-flow/transformations/multicast-transformation-editor.md).  
  
 Сведения о свойствах, которые можно задать программно, см. в разделе [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796).  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств компонента см. в разделе [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>См. также  
 [Поток данных](../../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
