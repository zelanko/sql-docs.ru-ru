---
title: "Активация интеграции PowerPivot для семейств веб-сайтов в ЦС | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 52fb43ddd40e432cb174c9d0794a3919fc48ff7a
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="activate-power-pivot-integration-for-site-collections-in-ca"></a>Активация интеграции PowerPivot для семейств веб-сайтов в ЦС
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
При использовании параметра установки существующей фермы для установки SQL Server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint необходимо включить интеграцию функций [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для определенных семейств веб-сайтов. Если надстройка [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint была установлена с параметром "Новый сервер", эту задачу можно пропустить, так как программа установки SQL Server уже активировала интеграцию компонента [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для корневого семейства веб-сайтов при настройке развертывания.  
  
 Активация компонента на уровне семейств веб-сайтов необходима для того, чтобы сделать страницы и шаблоны приложения доступными для веб-сайтов, в том числе страницы конфигурации для планового обновления данных и страницы приложений для библиотеки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Gallery и библиотек веб-каналов данных.  
  
 Необходимо включить интеграцию [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для всех семейств веб-сайтов, поддерживающих обработку запросов [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## <a name="prerequisites"></a>предварительные требования  
 Пользователь должен быть администратором семейства веб-сайтов.  
  
## <a name="activate-power-pivot-features"></a>Включение функций PowerPivot  
  
1.  На сайте SharePoint нажмите кнопку **Действия сайта**.  
  
     По умолчанию доступ к веб-приложениям SharePoint осуществляется через порт 80. Это означает, что часто доступен сайта SharePoint, введя http://\<имя компьютера > Открыть корневой коллекции сайтов.  
  
2.  Щелкните элемент **Настройки сайта**.  
  
3.  В области "Администрирование семейства веб-сайтов" щелкните ссылку **Возможности семейства узлов**.  
  
4.  Прокрутите страницу вниз до пункта **Функция семейства веб-сайтов для интеграции с [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**.  
  
5.  Нажмите кнопку **Активировать**.  
  
6.  Повторите эти действия для дополнительных семейств веб-сайтов, открыв каждый из сайтов и щелкнув **Действия сайта**.  
  
## <a name="see-also"></a>См. также  
 [Настройка и администрирование сервера Power Pivot в центре администрирования](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Первоначальная настройка (Power Pivot для SharePoint)](http://msdn.microsoft.com/en-us/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)   
 [Установка Power Pivot для SharePoint 2010](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f)  
  
  
