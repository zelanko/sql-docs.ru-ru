---
title: 'Занятие учебника Analysis Services 13: развертывание | Документы Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8ed155c0d3621c59e844e30d10dc7117e587a8f9
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="deploy"></a>Развертывание

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

На этом занятии вы настройку свойств развертывания; Указание сервера для развертывания и имя для модели. Затем развернуть модель на сервере. После развертывания модели, пользователи могут подключаться к нему с помощью клиентского приложения создания отчетов. Дополнительные сведения см. в разделе [развертыванию в Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy) и [развертывание решений табличной модели](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
Предполагаемое время выполнения этого занятия: **5 минут**.  
  
## <a name="prerequisites"></a>предварительные требования  

В этой статье является частью учебника по табличному моделированию, который необходимо изучать по порядку. Перед выполнением задач этого занятия, необходимо завершить предыдущее занятие: [занятии 12: анализ в Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md).  

> [!IMPORTANT]  
> Если развертывание Azure Analysis Services, необходимо иметь [разрешения администратора](https://docs.microsoft.com/azure/analysis-services/analysis-services-server-admins) на serever.  

> [!IMPORTANT]  
> Если установлен образец базы данных AdventureWorksDW на локальном сервере SQL и развертывании модели на сервере служб Azure Analysis Services, [локального шлюза данных](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway) является обязательным.
  
## <a name="deploy-the-model"></a>Развертывание модели  
  
#### <a name="to-configure-deployment-properties"></a>Настройка свойств развертывания  

  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Интернет-продаж AW** проекта, а затем нажмите кнопку **свойства**.  
  
2.  В **страницы свойств Интернет-продаж AW** диалогового **сервер развертывания**в **сервера** свойство, введите полное имя сервера. Если подключение к службам Analysis Services Azure, имя сервера должно inlcude полный URL-адрес.

    ![как lesson13-развертывание свойство](../tutorial-tabular-1400/media/as-lesson13-deploy-property.png)
  
3.  В **базы данных** введите **Интернет-продаж Adventure Works**.  
  
4.  В **Имя_модели** введите **модель Интернет-продаж Adventure Works**.  
  
5.  Убедитесь в том, что все выбрано правильно, и нажмите кнопку **ОК**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales"></a>Развертывание Интернет-продаж Adventure Works
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Интернет-продаж AW** проекта > **сборки**.  

2.  Щелкните правой кнопкой мыши **Интернет-продаж AW** проекта > **развернуть**.

    При развертывании в Azure Analysis Services, может быть предложено ввести вашей учетной записи. Введите учетную запись организации и пароль, например nancy@adventureworks.com. Это учетная запись должна быть в "Администраторы" на сервере.
  
    Развернуть диалогового окна появляется и отображает состояние развертывания метаданных и каждая таблица, включенная в модель.  
    
    ![как lesson13-развертывание status](../tutorial-tabular-1400/media/as-lesson13-deploy-status.png)
  
3. После успешного завершения развертывания нажмите кнопку **Закрыть**.  
  

В этом уроке описываются наиболее распространенный и простой способ развертывания табличной модели из SSDT. Параметры расширенного развертывания, например, мастер развертывания или автоматизация с XML для Аналитики и объекты AMO обеспечивают большую гибкость, согласованность и запланированных развертываний. Дополнительные сведения см. в разделе [развертывание решений табличной модели](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md).

## <a name="conclusion"></a>Заключение  
Поздравляем! По завершении вы сможете разработки и развертывания первой служб Analysis Services табличной модели. Этот учебник помог вам выполнить одну из самых распространенных задач в создании табличной модели. Теперь, когда модель интернет-продаж Adventure Works развернута, можно использовать среду SQL Server Management Studio для управления ею, создания скриптов обработки и плана резервного копирования. Пользователи теперь могут подключаться к модели с помощью клиентского приложения создания отчетов, таких как Microsoft Excel или Power BI.  

![как lesson13 ssms](../tutorial-tabular-1400/media/as-lesson13-ssms.png)
  
  
  
## <a name="whats-next"></a>Дальнейшие действия
[Подключиться с помощью Power BI Desktop](https://docs.microsoft.com/azure/analysis-services/analysis-services-connect-pbi)   
[Дополнительного занятия - динамической безопасности](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)   
[Дополнительного занятия - строки детализации](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)   
[Дополнительного занятия - неоднородные иерархии](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)   
