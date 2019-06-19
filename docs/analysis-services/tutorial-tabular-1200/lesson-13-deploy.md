---
title: Урок 13. Развертывание | Документация Майкрософт
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c20a0367612aee48c1a58e9cde8ba1a44d3fafc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65404806"
---
# <a name="lesson-13-deploy"></a>Урок 13. Развертывание
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

На этом занятии вы настроите свойства развертывания; Указание локально или экземпляр Azure сервера и имя для модели. Затем вы развернете модель к этому экземпляру. После развертывания модели, пользователи смогут подключаться к нему с помощью клиентского приложения для создания отчетов. Дополнительные сведения о развертывании см. в разделе [развертывание решений табличной модели](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md) и [развертывание в Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy).  
  
Предполагаемое время для выполнения этого занятия: **5 минут**  
  
## <a name="prerequisites"></a>предварительные требования  
Этот раздел является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [Занятие 12. Анализ в Excel](lesson-12-analyze-in-excel.md).  
  
## <a name="deploy-the-model"></a>Развертывание модели  
  
#### <a name="to-configure-deployment-properties"></a>Настройка свойств развертывания  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **AW Internet Sales** проекта, а затем нажмите кнопку **свойства**.  
  
2.  В **страницы свойств AW Internet Sales** диалогового **сервер развертывания**в **Server** свойство, введите имя сервера Azure Analysis Services или в локальном экземпляре сервера, работающем в табличном режиме. Это будет экземпляр сервера, который будет развернут модели.  

    ![консультанты развертывание развертывания server свойство](media/aas-deploy-deployment-server-property.png)
 
    > [!IMPORTANT]  
    > Необходимо иметь разрешения администратора на службы Analysis Services экземпляр в удаленном развертывании на нем.  
  
3.  В **базы данных** введите **Интернет-продаж Adventure Works**.  
  
4.  В **Имя_модели** введите **модель Интернет-продаж Adventure Works**.  
  
5.  Убедитесь в том, что все выбрано правильно, и нажмите кнопку **ОК**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>Развертывание табличной модели интернет-продаж Adventure Works  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **AW Internet Sales** проекта > **построения**.  

2.  Щелкните правой кнопкой мыши **AW Internet Sales** проекта > **развернуть**.

    При развертывании в Azure Analysis Services, вы вскоре скорее всего запрос на ввод учетной записи. Введите учетную запись организации и passsword, например nancy@adventureworks.com. Эта учетная запись должна обладать правами администратора на экземпляре сервера.
  
    Появится диалоговое окно «Развертывание», в котором будет отображено состояние развертывания метаданных, а также каждая таблица, включенная в модель.  
    
    ![консультанты развертывание status](media/aas-deploy-status.png)
  
3. После успешного завершения развертывания нажмите кнопку **Закрыть**.  
  
## <a name="conclusion"></a>Заключение  
Поздравляем! Вы заканчивается Создание и развертывание служб Analysis Services табличной модели. Этот учебник помог вам выполнить одну из самых распространенных задач в создании табличной модели. Теперь, когда модель интернет-продаж Adventure Works развернута, можно использовать среду SQL Server Management Studio для управления ею, создания скриптов обработки и плана резервного копирования. Пользователи теперь могут подключаться к модели с помощью клиентского приложения создания отчетов, таких как Microsoft Excel или Power BI.  

![как табличных lesson13-ssms](media/as-tabular-lesson13-ssms.png)
  
  
## <a name="see-also"></a>См. также  
[Режим DirectQuery](../tabular-models/directquery-mode-ssas-tabular.md)  
[Настройка моделирования данных по умолчанию и свойств развертывания](../tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[Базы данных табличной модели](../tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  ## <a name="whats-next"></a>Дальнейшие действия
*  [Дополнительное занятие. Реализация динамической безопасности с помощью фильтров строк](supplemental-lesson-implement-dynamic-security-by-using-row-filters.md).

*  [Дополнительное занятие — Настройка свойств отчетов для отчетов Power View](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md).
