---
title: "Занятие 14: Развертывание | Документы Microsoft"
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 213a5cb740899114c13d84305858a499759a8712
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-13-deploy"></a>Занятие 13. Развертывание
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии вы настроите свойства развертывания; Указание локальной или экземпляр сервера Azure и имя для модели. Затем вы развернете модели к этому экземпляру. После развертывания модели, пользователи могут подключаться к нему с помощью клиентского приложения создания отчетов. Дополнительные сведения о развертывании см. в разделе [развертывание решений табличной модели](../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md) и [развертыванию в Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy).  
  
Предполагаемое время выполнения этого занятия: **5 минут**.  
  
## <a name="prerequisites"></a>предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятии 12: анализ в Excel](../analysis-services/lesson-12-analyze-in-excel.md).  
  
## <a name="deploy-the-model"></a>Развертывание модели  
  
#### <a name="to-configure-deployment-properties"></a>Настройка свойств развертывания  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Интернет-продаж AW** проекта, а затем нажмите кнопку **свойства**.  
  
2.  В **страницы свойств Интернет-продаж AW** диалогового **сервер развертывания**в **сервера** свойство, введите имя сервера служб Azure Analysis Services или локального экземпляра сервера, работающего в табличном режиме. Это будет экземпляр сервера, который модели будут развернуты.  

    ![консультанты развертывание развертывания server свойство](../analysis-services/media/aas-deploy-deployment-server-property.png)
 
    > [!IMPORTANT]  
    > Необходимо иметь разрешения администратора на удаленной службы Analysis Services экземпляр в определенном порядке для развертывания к нему.  
  
3.  В **базы данных** введите **Интернет-продаж Adventure Works**.  
  
4.  В **Имя_модели** введите **модель Интернет-продаж Adventure Works**.  
  
5.  Убедитесь в том, что все выбрано правильно, и нажмите кнопку **ОК**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>Развертывание табличной модели интернет-продаж Adventure Works  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Интернет-продаж AW** проекта > **сборки**.  

2.  Щелкните правой кнопкой мыши **Интернет-продаж AW** проекта > **развернуть**.

    При развертывании служб Azure Analysis Services будет скорее всего приглашение укажите свою учетную запись. Введите учетную запись организации и passsword, например nancy@adventureworks.com. Это учетная запись должна быть в «Администраторы» на экземпляре сервера.
  
    Появится диалоговое окно «Развертывание», в котором будет отображено состояние развертывания метаданных, а также каждая таблица, включенная в модель.  
    
    ![Развертывание состояния консультанты](../analysis-services/media/aas-deploy-status.png)
  
3. После успешного завершения развертывания нажмите кнопку **Закрыть**.  
  
## <a name="conclusion"></a>Заключение  
Поздравляем! По завершении вы сможете разработки и развертывания первой служб Analysis Services табличной модели. Этот учебник помог вам выполнить одну из самых распространенных задач в создании табличной модели. Теперь, когда модель интернет-продаж Adventure Works развернута, можно использовать среду SQL Server Management Studio для управления ею, создания скриптов обработки и плана резервного копирования. Пользователи теперь могут подключаться к модели с помощью клиентского приложения создания отчетов, таких как Microsoft Excel или Power BI.  

![как табличных lesson13-ssms](../analysis-services/media/as-tabular-lesson13-ssms.png)
  
  
## <a name="see-also"></a>См. также раздел  
[Режим DirectQuery (табличные службы SSAS)](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)  
[Настройка моделирования данных по умолчанию и свойств развертывания (табличные службы SSAS)](../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[Базы данных табличной модели (табличные службы SSAS)](../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  ## <a name="whats-next"></a>Дальнейшие действия
*  [Дополнительного занятия - реализация динамической безопасности с помощью фильтров строк](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md).

*  [Дополнительное занятие — Настройка свойства отчетов для отчетов Power View](../analysis-services/supplemental-lesson-configure-reporting-properties-for-power-view-reports.md).
