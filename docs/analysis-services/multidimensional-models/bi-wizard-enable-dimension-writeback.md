---
title: "Включение обратной записи в измерение | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f8f2ddac65e4ffbb24118a498f96dad83c2c138d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="bi-wizard---enable-dimension-writeback"></a>Мастер бизнес-Аналитики — включить обратную запись в измерение
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Добавьте расширение обратной записи измерений к кубу или измерению, чтобы пользователи могли вручную изменять структуру и элементы измерения. Обновления измерений, доступных для записи, записываются прямо в таблицу измерения. Это расширение изменяет настройку свойства **WriteEnabled** для измерения.  
  
 Чтобы добавить обратную запись в измерение, используйте мастер бизнес-аналитики и выберите параметр **Включить обратную запись в измерение** на странице **Выбор расширения** . После этого мастер отобразит шаги, позволяющие выбрать измерение, к которому необходимо применить обратную запись, и установить этот параметр для выбранного измерения.  
  
> [!NOTE]  
>  Обратная запись поддерживается только для реляционных баз данных SQL Server и киосков данных.  
  
## <a name="selecting-a-dimension"></a>Выбор измерения  
 На первой странице **Включение обратной записи в измерение** мастера указывается измерение, к которому необходимо применить обратную запись. Добавление расширения обратной записи в измерение к этому выбранному измерению приведет к изменениям измерения. Эти изменения будут наследоваться всеми кубами, включающими выбранное измерение.  
  
## <a name="setting-dimension-writeback-capability"></a>Установка возможности обратной записи в измерение  
 На второй странице мастера — **Включение обратной записи в измерение** — непосредственно задается параметр **Включить обратную запись в измерение** . При выборе этого параметра свойство **WriteEnabled** измерения автоматически устанавливается равным **True**. При снятии этого флажка это свойство автоматически устанавливается равным **False**.  
  
## <a name="remarks"></a>Замечания  
 при создании нового элемента необходимо включить в измерение каждый атрибут. Нельзя вставить элемент, не указав значение ключевого атрибута измерения. Следовательно, на создание элементов оказывают влияние любые ограничения (такие как ключевые значения, отличные от NULL), установленные в таблице измерений; Необходимо также учитывать столбцы, дополнительно задаваемые такими свойствами измерения, как **CustomRollupColumn**, **CustomRollupPropertiesColumn** или **UnaryOperatorColumn** .  
  
> [!WARNING]  
>  При использовании SQL Azure в качестве источника данных для выполнения обратной записи в базу данных служб Analysis Services происходит сбой операции. Это сделано намеренно, поскольку параметр поставщика, разрешающий несколько активных результирующих наборов (MARS), не включен по умолчанию.  
>   
>  Для поддержки MARS и возможности обратной записи необходимо добавить следующий параметр в строку подключения:  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  Дополнительные сведения см. в разделе [Использование множественных активных результирующих наборов (MARS)](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
## <a name="see-also"></a>См. также:  
 [Измерения, доступные для записи](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
