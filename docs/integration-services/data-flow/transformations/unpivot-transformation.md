---
title: Преобразование отмены свертывания | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.unpivottrans.f1
- sql13.dts.designer.unpivottransformation.f1
helpviewer_keywords:
- Unpivot transformation
- more normalized data set [Integration Services]
- normalized data [Integration Services]
- datasets [Integration Services], normalized data
ms.assetid: f635c64b-a9c5-4f11-9c40-9cd9d5298c5d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6bd29508a760421722a776aa3924c3866bee79f6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65725742"
---
# <a name="unpivot-transformation"></a>Преобразование отмены свертывания

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Преобразование «Отмена свертывания» превращает набор ненормализованных данных в более нормализованную версию за счет развертывания значений из нескольких столбцов одной записи в несколько записей с теми же значениями в одном столбце. Например, набор данных с перечнем имен клиентов имеет одну строку для каждого клиента, при этом купленные товары и их количество отображаются в столбцах строки. После нормализации с помощью преобразования отмены свертывания набор данных содержит отдельную строку по каждому продукту, приобретенному клиентом.  
  
 На диаграмме ниже показан набор данных до преобразования «Отмена сведения» в столбце Product.  
  
 ![Набор данных после отмены сведения](../../../integration-services/data-flow/transformations/media/mw-dts-18.gif "Набор данных после отмены сведения")  
  
 На диаграмме ниже показан набор данных после преобразования «Отмена сведения» в столбце Product.  
  
 ![Набор данных до отмены сведения](../../../integration-services/data-flow/transformations/media/mw-dts-17.gif "Набор данных до отмены сведения")  
  
 В некоторых случаях результаты преобразования «Отмена свертывания» могут содержать строки с непредвиденными значениями. Например, если образец данных для отмены свертывания, показанных на диаграмме, содержит для пользователя Фреда во всех столбцах Qty значения NULL, то для Фреда выходные данные будут содержать только одну строку, а не пять. Столбец Qty будет содержать либо значение NULL, либо ноль в зависимости от типа данных столбца.  
  
## <a name="configuration-of-the-unpivot-transformation"></a>Настройка преобразования «Отмена сведения»  
 Преобразование «Отмена свертывания» включает пользовательское свойство **PivotKeyValue** . Это свойство может быть обновлено выражением свойства при загрузке пакета. Дополнительные сведения см. в разделах [Выражения служб Integration Services (SSIS)](../../../integration-services/expressions/integration-services-ssis-expressions.md), [Использование выражений свойств в пакетах](../../../integration-services/expressions/use-property-expressions-in-packages.md) и [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Это преобразование имеет один вход и один выход. Оно не имеет выхода ошибок.  
  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые вы можете задать в диалоговом окне **Расширенный редактор** или программными средствами, см. в следующих разделах.  
  
-   [Общие свойства](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Пользовательские свойства преобразований](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Дополнительные сведения о настройке свойств см. в разделе [Установление свойств компонента потока данных](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="unpivot-transformation-editor"></a>Редактор преобразования «Отмена свертывания»
  Используйте диалоговое окно **Редактор преобразования «Отмена свертывания»** , чтобы выбрать столбцы для сведения в строки, а также указать столбцы данных и новый выходной столбец сведенных значений.  
  
> [!NOTE]  
>  Этот раздел опирается на сценарий отмены свертывания, описанный в разделе [Unpivot Transformation](../../../integration-services/data-flow/transformations/unpivot-transformation.md) , чтобы проиллюстрировать использование параметров.  
  
### <a name="options"></a>Параметры  
 **Доступные входные столбцы**  
 Используя флажки, укажите столбцы, которые должны быть сведены в строки.  
  
 **Название**  
 Просмотрите имя доступного входного столбца.  
  
 **Передать**  
 Укажите, следует ли включить этот столбец в выход с отмененным сведением.  
  
 **Входной столбец**  
 Выберите для каждой строки столбец из списка доступных входных столбцов. Выбранные столбцы обозначаются флажками в таблице **Доступные входные столбцы** .  
  
 В сценарии отмены свертывания, описанном в разделе [Unpivot Transformation](../../../integration-services/data-flow/transformations/unpivot-transformation.md), входными столбцами являлись столбцы **Ham**, **Soda**, **Milk**, **Beer**и **Chips** .  
  
 **Целевой столбец**  
 Введите имя столбца данных.  
  
 В сценарии отмены свертывания, описанном в разделе [Преобразование отмены свертывания](../../../integration-services/data-flow/transformations/unpivot-transformation.md), целевым столбцом является столбец количества (**Qty**).  
  
 **Значение ключа сведения**  
 Введите имя значения сведения. По умолчанию, используется имя входного столбца, однако можно выбрать любое уникальное описательное имя.  
  
 Значение этого свойства можно задать с помощью выражения свойства.  
  
 В сценарии отмены свертывания, описанном в разделе [Unpivot Transformation](../../../integration-services/data-flow/transformations/unpivot-transformation.md), значения сведения представлены в новом столбце Product, обозначенном параметром **Имя столбца значений ключа сведения** , в виде текстовых значений **Ham**, **Soda**, **Milk**, **Beer**и **Chips**.  
  
 **Имя столбца значений ключа сведения**  
 Введите имя столбца значений ключа сведения. По умолчанию, используется «Значение ключа сведения», тем не менее можно выбрать любое уникальное описательное имя.  
  
 В сценарии отмены свертывания, описанном в разделе [Unpivot Transformation](../../../integration-services/data-flow/transformations/unpivot-transformation.md), именем столбца значений ключа сведения является **Product** , оно обозначает новый столбец **Product** , в который осуществляется отмена свертывания столбцов **Ham**, **Soda**, **Milk**, **Beer**и **Chips** .  
  
## <a name="see-also"></a>См. также:  
 [Справочник по сообщениям об ошибках служб Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Преобразование «Сведение»](../../../integration-services/data-flow/transformations/pivot-transformation.md)  
  
  
