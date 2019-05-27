---
title: Включение интеграции функций PowerPivot для семейств веб-сайтов в центре администрирования | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c5a8e3f2930d7975f8c75c8f89ab90b78461a650
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66072009"
---
# <a name="activate-powerpivot-feature-integration-for-site-collections-in-central-administration"></a>Активация интеграции функций PowerPivot для семейств веб-сайтов в центре администрирования
  При использовании параметра установки существующей фермы для установки SQL Server PowerPivot для SharePoint необходимо активировать интеграцию компонента PowerPivot для определенных семейств веб-сайтов. Если надстройка PowerPivot для SharePoint была установлена с параметром «Новый сервер», эту задачу можно пропустить, поскольку программа установки SQL Server уже активировала интеграцию компонента PowerPivot для корневого семейства веб-сайтов при настройке системы.  
  
 Активация компонента на уровне семейств веб-сайтов необходима, чтобы сделать страницы и шаблоны приложения доступными для веб-сайтов, в том числе страницы конфигурации для планового обновления данных страницы приложений для библиотеки PowerPivot Gallery и библиотек потоков данных.  
  
 Необходимо активировать интеграцию PowerPivot для всех семейств веб-сайтов, поддерживающих обработку запросов PowerPivot.  
  
## <a name="prerequisites"></a>предварительные требования  
 Пользователь должен быть администратором семейства веб-сайтов.  
  
## <a name="activate-powerpivot-features"></a>Активация функций PowerPivot  
  
1.  На сайте SharePoint нажмите кнопку **Действия сайта**.  
  
     По умолчанию доступ к веб-приложениям SharePoint осуществляется через порт 80. Это означает, что можно часто к сайту SharePoint, введя http://\<имя компьютера > Открыть корневой коллекции сайтов.  
  
2.  Щелкните элемент **Настройки сайта**.  
  
3.  В области "Администрирование семейства веб-сайтов" щелкните ссылку **Возможности семейства узлов**.  
  
4.  Прокрутите страницу вниз, пока не найдете **компонент коллекции сайтов для интеграции PowerPivot**.  
  
5.  Нажмите кнопку **Активировать**.  
  
6.  Повторите эти действия для дополнительных семейств веб-сайтов, открыв каждый из сайтов и щелкнув **Действия сайта**.  
  
## <a name="see-also"></a>См. также  
 [Настройка и администрирование сервера PowerPivot в центре администрирования](power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [Начальная конфигурация &#40;PowerPivot для SharePoint&#41;](../../sql-server/install/initial-configuration-powerpivot-for-sharepoint.md)   
 [Установка PowerPivot для SharePoint 2010](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
