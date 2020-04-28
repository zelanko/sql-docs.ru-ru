---
title: Master Data Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: db2e2fb2a174e73cfbe139c3ee15529af72e5b7b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176043"
---
# <a name="master-data-services"></a>Службы Master Data Services
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) — это решение [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] по управлению основными данными. Управление основными данными (master data management, MDM) включает в себя действия, предпринимаемые организацией для нахождения и определения нетранзакционных списков данных с целью компиляции управляемых главных списков. Проект MDM в основном предусматривает оценку и реструктуризацию внутренних бизнес-процессов, наряду с реализацией технологии MDM. Результатом успешно реализованного решения MDM становится получение надежных, централизованных данных, доступных для анализа, что влечет за собой принятие лучших бизнес-решений.

 После правильного обучения большинство бизнес-пользователей должны приобрести способность реализовать решение [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Кроме того, можно использовать MDS для управления любым доменом; это не ограничивается управлением списками клиентов, продуктов или учетных записей. При первой установке служб MDS она не включает структуру для всех доменов — вы определяете нужные домены, создавая для них модели.

 В число других функциональных возможностей служб Master Data Services входят иерархии, детализированная безопасность, транзакции, поддержка версий данных и бизнес-правила.

 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] включает следующие компоненты и средства.

-   [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] — средство, используемое для создания и настройки баз данных и веб-приложений служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].

-   [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] — веб-приложение, используемое для выполнения административных задач (таких как создание модели или бизнес-правила), к которому обращаются пользователи для обновления данных.

-   MDSModelDeploy.exe — средство, которое используется для создания пакетов объектов моделей и данных для последующего развертывания в других средах.

-   Веб-служба [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], с помощью которой разработчик может расширять или создавать пользовательские решения [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].

-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], который используется для управления данными и создания новых сущностей и атрибутов.

 Сводные сведения о ресурсах MDS см. на [портале SQL Server Master Data Services](https://go.microsoft.com/fwlink/?LinkID=214272).

|||
|-|-|
|**Просмотр содержимого по областям**<br /> ![Маленький значок папки с файлами](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [Master Data Services обзор](master-data-services-overview-mds.md)<br /><br /> ![Маленький значок папки](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [Master Data Services функции и задачи](../../2014/master-data-services/master-data-services-features-and-tasks.md)<br /><br /> ![Маленький значок папки с файлами](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [технический справочник (Master Data Services)](technical-reference-master-data-services.md)<br /><br /> ![Маленький значок папки с файлами](../../2014/integration-services/media/filefolder-small.gif "Маленький значок папки") [(Master Data Services)](develop/master-data-services-developer-documentation.md)||


