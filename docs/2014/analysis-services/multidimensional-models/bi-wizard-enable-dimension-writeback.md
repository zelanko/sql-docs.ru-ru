---
title: Включение обратной записи в измерение | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e9236bfbd945386aa249291b490ad41680a3ff5d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62700953"
---
# <a name="enable-dimension-writeback"></a>Разрешение обратной записи в измерение
  Добавьте расширение обратной записи в куб или измерение, чтобы пользователи могли вручную изменять структуру и элементы измерения. Обновления измерений, доступных для записи, записываются прямо в таблицу измерения. Это расширение изменяет настройку свойства `WriteEnabled` для измерения.  
  
 Чтобы добавить обратную запись в измерение, используйте мастер бизнес-аналитики и выберите параметр **Включить обратную запись в измерение** на странице **Выбор расширения** . После этого мастер отобразит шаги, позволяющие выбрать измерение, к которому необходимо применить обратную запись, и установить этот параметр для выбранного измерения.  
  
> [!NOTE]  
>  Обратная запись поддерживается только для реляционных баз данных SQL Server и киосков данных.  
  
## <a name="selecting-a-dimension"></a>Выбор измерения  
 На первой странице **Включение обратной записи в измерение** мастера указывается измерение, к которому необходимо применить обратную запись. Добавление расширения обратной записи в измерение к этому выбранному измерению приведет к изменениям измерения. Эти изменения будут наследоваться всеми кубами, включающими выбранное измерение.  
  
## <a name="setting-dimension-writeback-capability"></a>Установка возможности обратной записи в измерение  
 На второй странице мастера — **Включение обратной записи в измерение** — непосредственно задается параметр **Включить обратную запись в измерение** . При выборе этого параметра свойство `WriteEnabled` измерения автоматически устанавливается равным `True`. При снятии этого флажка это свойство автоматически устанавливается равным `False`.  
  
## <a name="remarks"></a>Примечания  
 при создании нового элемента необходимо включить в измерение каждый атрибут. Нельзя вставить элемент, не указав значение ключевого атрибута измерения. Следовательно, на создание элементов оказывают влияние любые ограничения (такие как ключевые значения, отличные от NULL), установленные в таблице измерений; Необходимо также учитывать столбцы, дополнительно задаваемые такими свойствами измерения, как `CustomRollupColumn`, `CustomRollupPropertiesColumn` или `UnaryOperatorColumn`.  
  
> [!WARNING]  
>  При использовании SQL Azure в качестве источника данных для выполнения обратной записи в базу данных служб Analysis Services происходит сбой операции. Это сделано намеренно, поскольку параметр поставщика, разрешающий несколько активных результирующих наборов (MARS), не включен по умолчанию.  
>   
>  Для поддержки MARS и возможности обратной записи необходимо добавить следующий параметр в строку подключения:  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  Дополнительные сведения см. в разделе [Использование множественных активных результирующих наборов (MARS)](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
## <a name="see-also"></a>См. также  
 [Измерения, доступные для записи](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
