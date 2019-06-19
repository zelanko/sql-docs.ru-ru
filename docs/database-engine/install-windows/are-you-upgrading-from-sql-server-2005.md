---
title: Вы выполняете обновление с версии SQL Server 2005, 2008 или 2008 R2? | Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ad40e66f-71fe-4ee6-9ce3-17127e7b1d7a
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: jroth
ms.openlocfilehash: 4813ca33bca9f03d94fe6f926a7af612b217fd90
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66795025"
---
# <a name="are-you-upgrading-from-sql-server-2005-2008-or-2008r2"></a>Вы выполняете обновление с версии SQL Server 2005, 2008 или 2008 R2?

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 Окончание расширенной поддержки для SQL Server — еще одна причина перейти на более новую версию SQL Server и на Базу данных SQL Azure. Обновление позволяет обеспечить безопасность и соответствие требованиям, достичь высокой производительности и оптимизировать инфраструктуру платформы данных.  
  
 Дополнительные сведения, инструкции и средства для планирования и автоматизации обновления или миграции см. в разделах [Прекращение поддержки SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005) и [Прекращение поддержки SQL Server 2008](https://www.microsoft.com/cloud-platform/windows-sql-server-2008).  
  
## <a name="why-upgrade"></a>Зачем выполнять обновление  
  
> [!IMPORTANT]  
>  Расширенная поддержка SQL Server 2005 закончилась 12 апреля 2016 г. Если SQL Server 2005 будет использоваться после 12 апреля 2016 г., вы больше не будете получать обновления для системы безопасности.  

> [!IMPORTANT]  
>  Расширенная поддержка SQL Server 2008 и 2008 R2 закончится 9 июля 2019 г. После этой даты SQL Server 2008 или 2008 R2 больше не будут получать обновления для системы безопасности. Дополнительные сведения см. в статье блога [Announcing New Options for SQL Server 2008](https://azure.microsoft.com/blog/announcing-new-options-for-sql-server-2008-and-windows-server-2008-end-of-support/) (Объявление о новых возможностях для SQL Server 2008).  
  
## <a name="choose-your-upgrade-option"></a>Выберите вариант обновления  
При обновлении реляционных баз данных из более ранних версий SQL Server доступны следующие варианты реляционного хранилища на платформе Майкрософт.  
  
Чтобы просмотреть более подробный анализ этих вариантов, [щелкните здесь](https://sql05upgrade.azurewebsites.net/).  
  
|Вариант реляционного хранилища|Преимущества|Другие факторы, которые следует учитывать|  
|-------------------------------|--------------|-------------------------------|  
|**SQL Server на локальном компьютере**<br /><br /> Этот вариант рекомендуется для приложений баз данных любого типа: от транзакционных систем до хранилищ данных.|У вас есть полный контроль над возможностями и масштабируемостью, так как вы управляете и оборудованием, и программным обеспечением.<br /><br /> Эта среда наиболее близка к среде более старого экземпляра SQL Server.|Необходимо сделать максимальные первоначальные инвестиции и обеспечить наиболее тщательное управление, поскольку необходимо приобрести собственное оборудование и программное обеспечение, поддерживать его и управлять им.<br /><br /> Дополнительные сведения см. на странице [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-rtm).|  
|**SQL Server, размещенный на виртуальных машинах Azure**<br /><br /> Рекомендуется использовать этот вариант, если требуется следующее.<br /><br /> Преимущества миграции в размещенную среду.<br /><br /> Управление операционной средой.<br /><br /> Набор знакомых функций SQL Server.|Можно быстро выполнить развертывание из библиотеки образов виртуальных машин.<br /><br /> Вы получаете полный набор функций SQL Server.<br /><br /> Можно сэкономить на стоимости оборудования и серверного программного обеспечения. Вы платите только за почасовое использование.|Необходимо настроить программное обеспечение SQL Server и операционной системы и управлять им.<br /><br /> <br /><br /> Дополнительные сведения см. в статье [Обзор SQL Server на виртуальных машинах Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).<br /><br /> Сведения о миграции см. в разделе [Перенос базы данных в SQL Server на виртуальной машине Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/).|  
|**Размещенная служба базы данных SQL Azure**<br /><br /> Рекомендуется использовать этот вариант, если требуется экономичное решение с меньшим объемом обслуживания.<br /><br /> Этот вариант особенно хорошо подходит для приложений, которым не требуется постоянное выделение одинаковых мощностей или для которых необходим внешний доступ.|Можно быстро выполнить развертывание и масштабирование.<br /><br /> Вы платите только за почасовое использование.<br /><br /> Стоимость обслуживания включает не только хранилище, но и высокую доступность и автоматическое резервное копирование.|В базе данных SQL Azure отсутствуют некоторые функции SQL Server, которые не применяются в размещенной облачной среде. Дополнительные сведения см. в разделе [Сведения о Transact-SQL Базы данных SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/).<br /><br /> Кроме того, База данных SQL Azure имеет максимальный размер 4 ТБ, а SQL Server — 524 ПБ. Дополнительные сведения: [Ограничения ресурсов для отдельных баз данных](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)<br /><br /> Дополнительные сведения о Базе данных SQL: [Общие сведения о Базе данных SQL Azure](https://azure.microsoft.com/services/sql-database/), [Документация по Базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/).<br /><br /> Сведения о миграции см. в статье, посвященной [переносу базы данных SQL Server в базу данных Azure SQL](https://azure.microsoft.com/documentation/articles/sql-database-cloud-migrate/).|  
  
 Возможно, для некоторых данных и приложений следует использовать нереляционное решение или решение, отличное от SQL.  
  
|Нереляционное решение|Преимущества|  
|------------------------------|--------------|  
|**Azure Cosmos DB**<br /><br /> Рекомендуем использовать этот вариант для современных, масштабируемых мобильных и веб-приложений, которые используют данные JSON и которым необходимо надежное выполнение запросов и обработка транзакционных данных.<br /><br /> Дополнительные сведения см. в разделе [Cosmos DB](https://azure.microsoft.com/services/cosmos-db/).<br /><br /> Сведения об импорте данных см. в статье [Импорт данных в Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/import-data/).|Документы индексируются, и для запросов к ним можно использовать знакомый синтаксис SQL.<br /><br /> База данных является бессхемной.<br /><br /> Можно добавлять свойства в документы без необходимости перестроения индексов.<br /><br /> Поддержка JSON и JavaScript осуществляется прямо внутри ядра СУБД.<br /><br /> Вы получаете встроенную поддержку геопространственных данных и интеграции с другими службами Azure, включая поиск Azure, HDInsight и фабрику данных.<br /><br /> Вы получаете высокопроизводительное хранилище с низкими задержками, имеющее зарезервированные уровни пропускной способности.|  
|**Табличное хранилище Azure**<br /><br /> Рекомендуется использовать этот вариант для хранения петабайт частично структурированных данных в экономичном решении.<br /><br /> Дополнительные сведения см. в разделе [Табличное хранилище](https://azure.microsoft.com/services/storage/tables/).|Можно развивать приложения и табличную схему без перевода данных в автономный режим.<br /><br /> Можно увеличивать масштаб без сегментирования набора данных.<br /><br /> Вы получаете географически избыточное хранилище, которое реплицирует данные по нескольким регионам.|  
  
## <a name="plan-your-upgrade"></a>Планирование обновления  
  
-   Запланировать обновление своего экземпляра SQL Server 2005 вам поможет следующая серия записей блога от команды разработчиков SQL Server. 
    - Планирование эффективного обновления SQL Server 2005: [шаг 1 из 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx), [шаг 2 из 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx), [шаг 3 из 3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)
- Подготовьтесь к [прекращению поддержки SQL Server 2008](https://www.microsoft.com/sql-server/sql-server-2008).
  
-   Ознакомьтесь с требованиями и рекомендациями в разделе [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md), включая [Требования к оборудованию и программному обеспечению для установки SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Ознакомьтесь со способами обновления.  
  
    -   Просмотрите доступные методы обновления и узнайте о способах планирования и тестирования в статье [Обновление [компонент ядра СУБД]](../../database-engine/install-windows/upgrade-database-engine.md).  
  
        > [!IMPORTANT]  
        >- Обновить экземпляр SQL Server 2005 до SQL Server 2017 на месте нельзя. Необходимо установить экземпляр SQL Server 2017, а затем перенести базы данных SQL Server 2005 в новую установку. Дополнительные сведения см. в разделе "Обновление новой установки" статьи [Выбор метода обновления компонента Database Engine](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
        >- Вы можете выполнить обновление SQL 2008 и SQL 2008 R2 "на месте" с переходом на SQL 2017. Дополнительные сведения см. в статье [Поддерживаемые обновления версий и выпусков](supported-version-and-edition-upgrades-2017.md). 


-    Дополнительные сведения, инструкции и средства для планирования и автоматизации обновления или миграции см. в разделах [Прекращение поддержки SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005) и [Прекращение поддержки SQL Server 2008](https://www.microsoft.com/cloud-platform/windows-sql-server-2008).  
  
## <a name="get-sql-server"></a>Получить SQL Server  
 Скачать ознакомительную версию SQL Server можно здесь: [Файлы для скачивания для SQL Server](https://www.microsoft.com/sql-server/sql-server-downloads).  
  
## <a name="next-steps"></a>Next Steps  
 [SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-2017)   
 [Прекращение поддержки SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005)   
 [Прекращение поддержки SQL Server 2008](https://www.microsoft.com/cloud-platform/windows-sql-server-2008)
  
  
