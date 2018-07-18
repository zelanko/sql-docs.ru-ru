---
title: 'Analysis Services занятие для учебника по 13: развертывание | Документация Майкрософт'
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
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37973086"
---
# <a name="deploy"></a>Развертывание

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

На этом занятии вы настроите свойства развертывания; Указание сервера для развертывания и имя для модели. Затем развернуть модель на сервер. После развертывания модели, пользователи смогут подключаться к нему с помощью клиентского приложения для создания отчетов. Дополнительные сведения см. в разделе [развертывание в Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy) и [развертывание решений табличной модели](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
Предполагаемое время выполнения этого занятия: **5 минут**.  
  
## <a name="prerequisites"></a>предварительные требования  

Эта статья входит в учебник по табличному моделированию, который следует изучать в порядке. Перед выполнением задач на этом занятии, необходимо завершить предыдущее занятие: [занятие 12: анализ в Excel](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md).  

> [!IMPORTANT]  
> Если развертывание служб Azure Analysis Services, необходимо иметь [разрешения администратора](https://docs.microsoft.com/azure/analysis-services/analysis-services-server-admins) на serever.  

> [!IMPORTANT]  
> Если вы установили образца базы данных AdventureWorksDW на локальном сервере SQL Server и развертываете модель на сервере служб Azure Analysis Services, [локальный шлюз данных](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway) является обязательным.
  
## <a name="deploy-the-model"></a>Развертывание модели  
  
#### <a name="to-configure-deployment-properties"></a>Настройка свойств развертывания  

  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **AW Internet Sales** проекта, а затем нажмите кнопку **свойства**.  
  
2.  В **страницы свойств AW Internet Sales** диалогового **сервер развертывания**в **Server** свойство, введите полное имя сервера. Если подключение к службам Azure Analysis Services, имя сервера необходимо указать полный URL-адрес.

    ![как lesson13-развертывание свойство](../tutorial-tabular-1400/media/as-lesson13-deploy-property.png)
  
3.  В **базы данных** введите **Интернет-продаж Adventure Works**.  
  
4.  В **Имя_модели** введите **модель Интернет-продаж Adventure Works**.  
  
5.  Убедитесь в том, что все выбрано правильно, и нажмите кнопку **ОК**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales"></a>Чтобы развернуть Интернет-продаж Adventure Works
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **AW Internet Sales** проекта > **построения**.  

2.  Щелкните правой кнопкой мыши **AW Internet Sales** проекта > **развернуть**.

    При развертывании в Azure Analysis Services, может быть предложено ввести вашей учетной записи. Введите учетную запись организации и пароль, например nancy@adventureworks.com. Эта учетная запись должна обладать правами администратора на сервере.
  
    Диалоговое окно развертывания, в котором отобразится состояние развертывания метаданных и каждая таблица, включенная в модели.  
    
    ![как lesson13-развертывание status](../tutorial-tabular-1400/media/as-lesson13-deploy-status.png)
  
3. После успешного завершения развертывания нажмите кнопку **Закрыть**.  
  

В этом занятии описывается самый популярный и простой способ развертывания табличной модели из SSDT. Дополнительные параметры развертывания в мастере развертывания или автоматизация с помощью XML для Аналитики и объекты AMO обеспечивают большую гибкость, согласованности и выполнять развертывание по расписанию. Дополнительные сведения см. в разделе [развертывание решений табличной модели](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md).

## <a name="conclusion"></a>Заключение  
Поздравляем! Вы заканчивается Создание и развертывание служб Analysis Services табличной модели. Этот учебник помог вам выполнить одну из самых распространенных задач в создании табличной модели. Теперь, когда модель интернет-продаж Adventure Works развернута, можно использовать среду SQL Server Management Studio для управления ею, создания скриптов обработки и плана резервного копирования. Пользователи теперь могут подключаться к модели с помощью клиентского приложения создания отчетов, таких как Microsoft Excel или Power BI.  

![как lesson13 ssms](../tutorial-tabular-1400/media/as-lesson13-ssms.png)
  
  
  
## <a name="whats-next"></a>Дальнейшие действия
[Подключение с помощью Power BI Desktop](https://docs.microsoft.com/azure/analysis-services/analysis-services-connect-pbi)   
[Дополнительное занятие. динамическая безопасность](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)   
[Дополнительное занятие. строки детализации](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)   
[Дополнительное занятие. неоднородные иерархии](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)   
