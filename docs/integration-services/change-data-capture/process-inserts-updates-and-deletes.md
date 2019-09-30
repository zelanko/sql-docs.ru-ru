---
title: Обработка операций вставки, обновления и удаления | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],processing data
ms.assetid: 13a84d21-2623-4efe-b442-4125a7a2d690
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 035c31286e0594763c1063b606ad56473c41fbf5
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71294609"
---
# <a name="process-inserts-updates-and-deletes"></a>Обработка операций вставки, обновления и удаления

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  В потоке данных пакета служб Integration Services, выполняющего добавочную загрузку информации об измененных данных, второй задачей является разделение вставок, обновлений и удалений. Затем можно использовать соответствующие команды, чтобы применить их к назначению.  
  
> [!NOTE]  
>  Первой задачей в проектировании потока данных пакета, выполняющего добавочную загрузку измененных данных, является настройка исходного компонента, который запрашивает измененные данные. Дополнительные сведения об этом компоненте см. в разделе [Получение и интерпретация измененных данных](../../integration-services/change-data-capture/retrieve-and-understand-the-change-data.md). Описание общего процесса создания пакета, выполняющего добавочную загрузку информации об изменениях, см. в разделе [Система отслеживания измененных данных (SSIS)](../../integration-services/change-data-capture/change-data-capture-ssis.md).  
  
## <a name="associating-friendly-values-to-separate-inserts-updates-and-deletes"></a>Связывание понятных значений для разделения операций вставки, обновления и удаления  
 В приведенном примере извлечения измененных данных функция **cdc.fn_cdc_get_net_changes_<экземпляр_отслеживания>** возвращает только столбец метаданных с именем **__$operation**. Этот столбец метаданных содержит порядковое значение, которое указывает операцию, вызвавшую изменение.  
  
> [!NOTE]  
>  Дополнительные сведения о запросе, использующем вызовы функции **cdc.fn_cdc_get_net_changes_<экземпляр_отслеживания>** , см. в статье [Создание функции для получения информации об изменениях](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md).  
  
 Связать порядковое значение с соответствующей операцией сложнее, чем использовать мнемонический код операции. Например, «D» может представлять операцию удаления, а «I» — операцию вставки. В примере запроса, созданном в разделе [Создание функции для получения измененных данных](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md), порядковое значение преобразуется в понятное строковое значение, которое возвращается в новом столбце. Это преобразование показано в следующем сегменте кода:  
  
```sql
select   
    ...  
    case __$operation  
        when 1 then 'D'  
        when 2 then 'I'  
        when 4 then 'U'  
        else null  
     end as CDC_OPERATION  
```  
  
## <a name="configuring-a-conditional-split-transformation-to-direct-inserts-updates-and-deletes"></a>Настройка преобразования «Условное разбиение» для направления операций вставки, обновления и удаления в разные выходы  
 Если требуется направить строки измененных данных на один из трех выходов, преобразование «Условное разбиение» подходит идеально. Это преобразование проверяет значение столбца **CDC_OPERATION** в каждой строке и определяет, было изменение вставкой, обновлением или удалением.  
  
> [!NOTE]  
>  Столбец CDC_OPERATION содержит понятное строковое значение, полученное из числового значения в столбце **__$operation** .  
  
#### <a name="to-split-inserts-updates-and-deletes-for-processing-by-using-a-conditional-split-transformation"></a>Разбиение операций вставки, обновления и удаления для обработки с помощью преобразования «Условное разбиение»  
  
1.  На вкладке **Поток данных** добавьте преобразование «Условное разбиение».  
  
2.  Соедините выход источника OLE DB с преобразованием «Условное разбиение».  
  
3.  На нижней панели **Редактора преобразования «Условное разбиение»** введите три следующие строки, чтобы обозначить три выхода.  
  
    1.  Введите строку с условием `CDC_OPERATION == "I"` , чтобы направить вставленные строки на выход для вставок.  
  
    2.  Введите строку с условием `CDC_OPERATION == "U"` , чтобы направить обновленные строки на выход для обновлений.  
  
    3.  Введите строку с условием `CDC_OPERATION == "D"` , чтобы направить удаленные строки на выход для удалений.  
  
## <a name="next-step"></a>Следующий шаг  
 Когда строки разбиты для обработки, следующим шагом является применение изменений к назначению.  
  
 **Следующая статья:** [Применение изменений в назначении](../../integration-services/change-data-capture/apply-the-changes-to-the-destination.md)  
  
## <a name="see-also"></a>См. также:  
 [Преобразование «Условное разбиение»](../../integration-services/data-flow/transformations/conditional-split-transformation.md)   
 [Разбиение набора данных с помощью преобразования «Условное разбиение»](../../integration-services/data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
