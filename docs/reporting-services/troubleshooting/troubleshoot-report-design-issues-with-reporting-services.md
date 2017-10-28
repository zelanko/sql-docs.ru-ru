---
title: "Устранение проблем проектирования отчетов со службами Reporting Services | Документы Microsoft"
ms.custom: 
ms.date: 02/27/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0d103da-5a3e-475c-a71a-9e23476095e2
caps.latest.revision: 5
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7646ed9709e6d293b3e72a0255efc2f3bc17eebf
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="troubleshoot-report-design-issues-with-reporting-services"></a>Устранение проблем проектирования отчетов с помощью служб Reporting Services
Проблемы проектирования отчетов могут возникать при создании макета отчета с помощью конструктора в приложении разработки отчетов. Этот раздел помогает устранять эти проблемы.   
  
## <a name="why-does-my-text-box-show-only-a-single-value-and-not-repeat-for-every-row"></a>Почему в текстовом поле отображается только одно значение, и оно не повторяется для каждой строки?  
Текстовое поле со ссылкой на поле набора данных подготавливается только один раз и отображает первое значение в наборе данных.   
  
**Родительским элементом текстового поля является тело отчета**  
  
  
Текстовое поле, добавленное непосредственно в область конструктора, может отображать только статистическое значение для набора данных.  
  
Для проверки родительского контейнера текстового поля выберите текстовое поле и в панели свойств прокрутите до **родительского элемента**.   
  
Если необходимы текстовые поля, показывающие каждое значение в наборе данных, используйте область данных, такую как таблицу или матрицу. По умолчанию каждая ячейка в таблице или матрице содержит текстовое поле. Перетащите поля набора данных во все ячейки.   
  
## <a name="why-cant-i-add-total-pages-to-my-report"></a>Почему в отчет нельзя добавить общее число страниц?  
Встроенные поля `[&PageNumber]` и `[&TotalPages]` в тексте отчета недопустимы.   
  
Поля PageNumber и TotalPages допустимы только в верхнем и нижнем колонтитулах.  
  
  
Встроенные поля [&PageNumber] и [&TotalPages] допустимы только в верхнем и нижнем колонтитулах.   
  
Чтобы добавить в отчет поле [&PageNumber] или [&TotalPages], необходимо вначале добавить верхний или нижний колонтитул. Дополнительные сведения см. в разделе [Добавление или удаление верхнего или нижнего колонтитула страницы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/add-or-remove-a-page-header-or-footer-report-builder-and-ssrs.md).  
  
> [!NOTE]  
> Включение поля [&TotalPages] в верхний или нижний колонтитул может иметь определенные последствия с точки зрения обработки отчета. Дополнительные сведения см. в разделе "Устранение неполадок отчетов: экспорт отчетов в файл определенного формата".  
[Troubleshoot Processing of Reporting Services Reports](../../reporting-services/troubleshooting/troubleshoot-processing-of-reporting-services-reports.md)(Устранение неполадок при обработке отчетов служб Reporting Services).  
  
## <a name="how-do-i-design-two-tables-or-a-chart-and-a-table-to-display-side-by-side"></a>Как спроектировать одновременное отображение рядом двух таблиц или диаграммы и таблицы?  
Проектирование отчета не отвечает требованиям WYSIWYG (режим наглядного отображения). Обработчик отчетов объединяет данные, элементы отчета, сведения о макете отчета, такие как пустое пространство, контейнеры и выражения, для создания скомпилированного отчета, передаваемого после этого в модуль подготовки отчетов, который форматирует этот отчет для указанного способа просмотра: в интерактивном виде для HTML-браузера или в виде файла в определенном формате. Автоматические алгоритмы форматирования могут создать макет отчета, который потребуется изменить.   
  
### <a name="rendering-rules-use-page-size-containers-peer-objects-relative-placement-and-white-space-to-determine-layout"></a>Правила подготовки для определения макета используют размер страницы, контейнеры, одноранговые объекты, относительное смещение и пустое пространство  
Обычно рост отчета происходит в соответствии с данными в нем, при этом другие элементы отчета вытесняются.   
  
Чтобы сгруппировать вместе области данных или элементы отчета, поместите их в один родительский контейнер. Например, поместите диаграмму и таблицу в прямоугольный контейнер и выровняйте их верхние края так, чтобы они отображались рядом. Дополнительные сведения см. в статье [Поведение при подготовке к просмотру (построитель отчетов и службы SSRS)](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также  
[Устранение неполадок при извлечении данных с помощью отчетов служб Reporting Services](../../reporting-services/troubleshooting/troubleshoot-data-retrieval-issues-with-reporting-services-reports.md)  
[Устранение неполадок, связанных с подписками и доставкой служб Reporting Services](../../reporting-services/troubleshooting/troubleshoot-reporting-services-subscriptions-and-delivery.md)  
  
  
  

[!INCLUDE[feedback_stackoverflow_msdn_connect](../../includes/feedback-stackoverflow-msdn-connect.md)]


