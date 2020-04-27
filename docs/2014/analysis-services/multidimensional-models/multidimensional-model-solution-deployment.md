---
title: Развертывание решения многомерной модели | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, planning
- deploying [Analysis Services]
- deploying [Analysis Services], planning
ms.assetid: 7259c201-ff54-43e8-bda5-a6d51474e0e6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9ec674c1eb64f2e5191df600864fa38aa3da0749
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66073552"
---
# <a name="multidimensional-model-solution-deployment"></a>Развертывание решений многомерных моделей
  После завершения разработки проекта [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] базу данных можно развернуть на сервере служб Analysis Services. Службы Analysis Services предоставляют шесть возможных методов развертывания, которые могут быть использованы для перемещения базы данных на тестовый или рабочий сервер. Ниже эти методы перечислены в порядке приоритетности: автоматизация объектов AMO, XML для аналитики, мастер развертывания, программа развертывания, мастер синхронизации, резервное копирование и восстановление.  
  
 Этот раздел включает следующие подразделы:  
  
 [Методы развертывания](#bkmk_meth)  
  
 [Рекомендации по развертыванию](#bkmk_considerations)  
  
 [Связанные задачи](#bkmk_rel)  
  
##  <a name="deployment-methods"></a><a name="bkmk_meth"></a>Методы развертывания  
  
|Метод|Описание|Ссылка|  
|------------|-----------------|----------|  
|**Автоматизация объектов управления аналитикой (объектов AMO)**|Объекты AMO предоставляют программный интерфейс с полным набором команд для служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], включая команды, которые можно использовать для развертывания решения. Автоматизация объектов AMO как один из подходов к развертыванию решения представляет собой наиболее гибкий метод, для реализации которого, однако, требуются определенные трудозатраты в части программирования.  Ключевое преимущество использования объектов AMO заключается в возможности использования агента SQL Server Agent вместе с AMO-приложением для запуска развертывания по заданному расписанию.|[Разработка объектов управления аналитикой (объекты AMO)](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)|  
|**XML для аналитики**|Используйте [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для создания скрипта XMLA метаданных существующей базы данных [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , а затем запустите этот скрипт на другом сервере для воссоздания исходной базы данных. Скрипты XMLA легко формируются в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , для чего сначала нужно задать процесс развертывания, затем кодифицировать его и сохранить в скрипте XMLA. После сохранения в виде файла скрипт XMLA можно легко запустить в соответствии с расписанием или внедрить скрипт в приложение, подключающееся непосредственно к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].<br /><br /> На основе заранее заданных настроек можно выполнять и скрипты XMLA, используя с этой целью агент SQL Server, но при этом пользователь не может использовать скрипты XMLA с той же гибкостью, что и объекты AMO. Объекты AMO обеспечивают большую функциональность, предоставляя доступ к полному спектру административных команд.|[Развертывание решений модели с помощью XMLA](deploy-model-solutions-using-xmla.md)|  
|**Мастер развертывания**|Используйте мастер развертывания и выходные файлы XML для аналитики, созданные проектом [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , для развертывания метаданных проекта на целевом сервере. При помощи мастера развертывания можно выполнять развертывание непосредственно из файла служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , создаваемого выходным каталогом по конструкции проекта.<br /><br /> Основное преимущество использования мастера развертывания [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] — это удобство. По аналогии с тем, что можно сохранить скрипт XMLA для последующего использования в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], можно сохранять и скрипты мастера развертывания. Мастер развертывания можно запускать как интерактивно, так и из командной строки при помощи программы развертывания.|[Развертывание решений модели с использованием мастера развертывания](deploy-model-solutions-using-the-deployment-wizard.md)|  
|**Программа развертывания**|Программа развертывания позволяет запустить подсистему развертывания служб Analysis Services из командной строки.|[Развертывание решений моделей с использованием программы развертывания](deploy-model-solutions-with-the-deployment-utility.md)|  
|**мастер синхронизации баз данных**|Воспользуйтесь мастером синхронизации баз данных для синхронизации метаданных и данных любых двух баз данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .<br /><br /> Мастер синхронизации можно использовать для копирования как данных, так и метаданных из исходного сервера на целевой сервер. Если на целевом сервере нет копии базы данных, которую необходимо развернуть, новая база данных будет скопирована на целевой сервер. Если на целевом сервере уже есть копия той же базы данных, база данных на целевом сервере будет обновлена для использования метаданных и данных базы данных-источника.|[Синхронизация баз данных служб Analysis Services](synchronize-analysis-services-databases.md)|  
|**Резервное копирование и восстановление**|Функция создания резервной копии представляет собой самый простой способ переноса баз данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . В диалоговом окне **Резервное копирование** можно задать конфигурацию параметров, а затем, не выходя из диалогового окна, запустить резервное копирование. Или можно создать скрипт, который можно сохранить для последующего многократного выполнения.<br /><br /> Создание резервной копии и восстановление не используются так же часто, как другие способы развертывания, однако позволяют быстро выполнить развертывание с минимальными инфраструктурными требованиями.|[Создание и восстановление резервных копий баз данных служб Analysis Services](backup-and-restore-of-analysis-services-databases.md)|  
  
##  <a name="deployment-considerations"></a><a name="bkmk_considerations"></a>Рекомендации по развертыванию  
 Перед развертыванием проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] определите, какие из следующих вопросов применяются к вашему решению, а затем ознакомьтесь с указанным по ссылке материалом для изучения способов решения проблемы.  
  
|Оценка|Ссылка на дополнительные сведения|  
|-------------------|------------------------------|  
|Какое оборудование и программные ресурсы требуются для этого решения?|[Требования и вопросы, связанные с развертыванием служб Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)|  
|Как вы будете развертывать дополнительные объекты, выходящие за рамки проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , такие как пакеты, отчеты и схемы реляционных баз данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ?||  
|Как загружать и обновлять данные в развернутой базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ?<br /><br /> Как вы будете обновлять метаданные (например, вычисления) в развернутой базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ?|[Методы развертывания](#bkmk_meth) в этом разделе.|  
|Нужно ли предоставлять пользователям доступ к данным служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] через Интернет?|[Настройка HTTP-доступа к службам Analysis Services в службах Internet Information Services (IIS) 8.0](../instances/configure-http-access-to-analysis-services-on-iis-8-0.md)|  
|Нужно ли предоставлять запросам возможность непрерывного доступа к данным служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ?|[Требования и вопросы, связанные с развертыванием служб Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)|  
|Нужно ли развертывать объекты в распределенной среде при помощи связанных объектов или удаленных секций?|[Создание локальной секции и управление ею (службы Analysis Services)](create-and-manage-a-local-partition-analysis-services.md), [Создание удаленной секции и управление ею (службы Analysis Services)](create-and-manage-a-remote-partition-analysis-services.md) и [Связанные группы мер](linked-measure-groups.md).|  
|Как вы будете обеспечивать безопасность данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ?|[Предоставление доступа к объектам и операциям (службы Analysis Services)](authorizing-access-to-objects-and-operations-analysis-services.md)|  
  
##  <a name="related-tasks"></a><a name="bkmk_rel"></a> Связанные задачи  
 [Требования и вопросы, связанные с развертыванием служб Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)  
  
 [Развертывание решений модели с помощью XMLA](deploy-model-solutions-using-xmla.md)  
  
 [Развертывание решений модели с использованием мастера развертывания](deploy-model-solutions-using-the-deployment-wizard.md)  
  
 [Развертывание решений моделей с использованием программы развертывания](deploy-model-solutions-with-the-deployment-utility.md)  
  
  
