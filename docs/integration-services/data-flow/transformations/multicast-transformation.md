---
title: Преобразование "Многоадресная доставка" | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.multicasttrans.f1
- sql13.dts.designer.multicasttransformation.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6fca2fd4670fae2838eb0512c68483024bdb4dee
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71297839"
---
# <a name="multicast-transformation"></a>преобразование «Многоадресная доставка»

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Преобразование «Многоадресная доставка» распределяет данные на входе на один или более выходов. Это преобразование схоже с преобразованием «Условное разбиение». Оба вида преобразований направляют данные на входе на несколько выходов. Их различие состоит в том, что преобразование «Многоадресная доставка» направляет каждую строку на все выходы, а преобразование «Условное разбиение» направляет одну строку на один выход. Дополнительные сведения см. в статье [Conditional Split Transformation](../../../integration-services/data-flow/transformations/conditional-split-transformation.md).  
  
 Можно производить настройку преобразования «Многоадресная доставка» путем добавления выходов.  
  
 Используя преобразование «Многоадресная доставка», пакет может создавать логические копии данных. Эта возможность полезна, если пакету необходимо применить несколько наборов преобразований к одним и тем же данным. Например, одна копия данных статистически обрабатывается и в назначение загружается только сводная информация, а в другую копию данных перед загрузкой в назначение добавляются значения уточняющего запроса и производные столбцы.  
  
 Это преобразование имеет один вход и несколько выходов. Вывод ошибок не поддерживается.  
  
## <a name="configuration-of-the-multicast-transformation"></a>Настройка преобразования «Многоадресная доставка»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Сведения о свойствах, которые можно задать программно, см. в разделе [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796).  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств компонента см. в разделе [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="multicast-transformation-editor"></a>редактор преобразования «Многоадресная доставка»
  Используйте диалоговое окно **Редактор преобразования «Многоадресная доставка»** , чтобы посмотреть и установить свойства для каждого выхода преобразования.  
  
### <a name="options"></a>Параметры  
 **Выходные данные**  
 Выберите вывод слева, чтобы посмотреть его свойства в таблице справа.  
  
 **Свойства**  
 Все перечисленные выходные свойства доступны только для чтения, за исключением свойств **Имя** и **Описание**.  
  
## <a name="see-also"></a>См. также:  
 [Поток данных](../../../integration-services/data-flow/data-flow.md)   
 [Преобразования служб Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
