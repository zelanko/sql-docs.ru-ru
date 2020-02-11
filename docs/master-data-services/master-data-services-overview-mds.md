---
title: Обзор
ms.custom: ''
ms.date: 02/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
keywords:
- what is master data
helpviewer_keywords:
- Master Data Services, overview
- Master Data Services
ms.assetid: 8a4c28b1-6061-4850-80b6-132438b8c156
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 44723e33929c71b51cdf61d675644a4bf9f6068d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729052"
---
# <a name="master-data-services-overview-mds"></a>Общие сведения о службах Master Data Services (MDS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом разделе описаны ключевые функции организации данных и управления ими с помощью [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. 
  
 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]позволяет управлять главным набором данных Организации. Можно организовывать данные в модели, создавать правила для обновления данных и контролировать тех, кто обновляет данные. Excel позволяет использовать основной набор данных совместно с другими людьми в вашей организации. 
  
 >  Описание архитектуры [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] см. в статье [Master Data Services — основы](https://www.simple-talk.com/sql/database-delivery/master-data-services-basics) на сайте simple-talk.com. Сведения о новых возможностях в [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]см. в разделе [новые возможности Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md)  
   **Инструкции по установке [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], настройке базы данных и веб-сайта, а также развертыванию образцов моделей см** . в разделе [Master Data Services Установка и настройка](../master-data-services/master-data-services-installation-and-configuration.md).  
  
 В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]модель является наивысшим уровнем контейнера в структуре основных данных. Можно создать модель для управления группами сходных данных, например для управления данными продуктов в сети. В модели содержится одна или несколько сущностей, а сущности содержат элементы, которые являются записями данных. Сущность похожа на таблицу.  
  
 Модель продукта в сети может содержать сущности, такие как продукт, цвет и стиль. Сущность цвета может содержать элементы для красного, серебряного и черного цвета.  
  
 ![Сущность цвета](../master-data-services/media/mds-productmodel-colorentity-composite.png "Сущность цвета")  
  
 Модели также содержат атрибуты, определенные в сущностях. Атрибут содержит значения, которые помогают описывать элементы сущности. Существуют атрибуты в свободной форме и атрибуты на основе домена.  Атрибут на основе домена содержит значения, которые заполняются элементами из сущности и могут использоваться как значения атрибутов для других сущностей.  
  
 Например, в сущности продукта могут иметься атрибуты в свободной форме для стоимости и веса. И существует атрибут на основе домена для цветового ![номера 1](../master-data-services/media/mds-number1.png "Номер 1") , который содержит значения, заполняемые элементами сущности Color. Этот главный список цветов используется в качестве значений атрибутов для сущности Product ![номер 2](../master-data-services/media/mds-number2.png "Номер 2").  
  
 ![Атрибут для цвета на основе домена](../master-data-services/media/mds-productentity-color-domainattribute.png "Атрибут для цвета на основе домена")  
  
 Производные иерархии происходят от связей между сущностями в модели. Это связи атрибутов на основе домена. Например, в модели продукта можно иметь цвет производной иерархии ![номер 1](../master-data-services/media/mds-number1.png "Номер 1") , поступающий из связи между сущностями номер цвета ![2](../master-data-services/media/mds-number2.png "Номер 2") и номер продукта ![3](../master-data-services/media/mds-number3.png "Номер 3") .  
  
 ![Производная иерархия цветов](../master-data-services/media/mds-derivedhierarchy.png "Производная иерархия цветов")  
  
 После определения базовой структуры данных можно начать добавление записей данных (элементов) с помощью функции импорта. Загрузите данные в промежуточные таблицы, проверьте данные с помощью бизнес-правил и загрузите данные в таблицы MDS.  Также можно использовать бизнес-правила для задания значений атрибутов.  
  
 В следующей таблице описываются основные задачи [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Если не указано другое, для всех следующих процедур необходимо иметь права администратора модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
> [!NOTE]  
>  Следующие задачи можно выполнить в тестовой среде и использовать предложенные образцы данных при установке служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Дополнительные сведения см. в разделе [Развертывание моделей (службы Master Data Services)](../master-data-services/deploying-models-master-data-services.md).  
  
|Действие|Сведения|Связанные темы|  
|------------|-------------|--------------------|  
|Создание модели|При создании модели она считается версией VERSION_1.|[Модели &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)<br /><br /> [Создание &#40;модели Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md)|  
|Создание сущностей|Создавайте столько сущностей, сколько необходимо для хранения элементов.|[Сущности &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)<br /><br /> [Создание сущности &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)|  
|Создание сущностей для использования в качестве атрибутов на основе домена|Чтобы создать атрибут на основе домена, сначала нужно создать сущность для заполнения списка значений атрибута.|[Атрибуты на основе домена &#40;Master Data Services&#41;](../master-data-services/domain-based-attributes-master-data-services.md)<br /><br /> [Создание атрибута на основе домена &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)|  
|Создание атрибутов для сущностей|Атрибуты создаются для описания элементов. Атрибуты Name и Code автоматически включаются в каждую сущность, и их нельзя удалить. Можно создать другие атрибуты в свободной форме для хранения текста, дат, чисел или файлов.|[Master Data Services &#40;атрибутов&#41;](../master-data-services/attributes-master-data-services.md)<br /><br /> [Создание текстового атрибута &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md)<br /><br /> [Создание числового атрибута &#40;Master Data Services&#41;](../master-data-services/create-a-numeric-attribute-master-data-services.md)<br /><br /> [Создание атрибута даты &#40;Master Data Services&#41;](../master-data-services/create-a-date-attribute-master-data-services.md)<br /><br /> [Создайте &#40;Master Data Services атрибута ссылки&#41;](../master-data-services/create-a-link-attribute-master-data-services.md)<br /><br /> [Создание атрибута файла &#40;Master Data Services&#41;](../master-data-services/create-a-file-attribute-master-data-services.md)|  
|Создание групп атрибутов|При наличии четырех или пяти атрибутов для сущности можно создавать группы атрибутов. Эти группы представлены вкладками наверху сетки в **Обозревателе** и упрощают навигацию за счет группирования атрибутов на отдельных вкладках.|[Группы атрибутов &#40;Master Data Services&#41;](../master-data-services/attribute-groups-master-data-services.md)<br /><br /> [Создание группы атрибутов &#40;Master Data Services&#41;](../master-data-services/create-an-attribute-group-master-data-services.md)|  
|Импорт элементов для поддерживающих сущностей|Данные для поддерживающих сущностей импортируются с использованием промежуточного процесса. Для модели Product это может означать импорт цветов или размеров. Элементы также можно создавать вручную.<br /><br /> <br /><br /> Примечание. Пользователи могут создавать элементы в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , если у них есть как минимум разрешение на **обновление** конечного объекта модели сущности и доступ к функциональной области **Обозреватель** .|[Обзор. Импорт данных из таблиц &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)<br /><br /> [Создание конечного элемента &#40;Master Data Services&#41;](../master-data-services/create-a-leaf-member-master-data-services.md)|  
|Создание и применение бизнес-правил, обеспечивающих высокое качество данных|Для гарантии точности данных создаются и публикуются бизнес-правила. Бизнес-правила можно использовать в следующих целях:<br /><br /> установка значений атрибута по умолчанию;<br /><br /> изменение значений атрибута;<br /><br /> отправка уведомлений по электронной почте, если данные не проходят проверку на соответствие бизнес-правилам.|[Бизнес-правила &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)<br /><br /> [Создание и публикация бизнес-правила &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)<br /><br /> [Подтверждение конкретных членов, обнаруженных при проверке на соответствие бизнес-правилам (службы Master Data Services)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)<br /><br /> [Настройка уведомлений по электронной почте &#40;Master Data Services&#41;](../master-data-services/configure-email-notifications-master-data-services.md)<br /><br /> [Настройка бизнес-правил для отправки уведомлений &#40;Master Data Services&#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)|  
|Импорт элементов для основных сущностей и применение бизнес-правил|Элементы для основных сущностей импортируются с использованием промежуточного процесса. По окончании импорта следует проверить версию, что включает применение бизнес-правил ко всем элементам версии модели.<br /><br /> После этого можно исправить выявленные проблемы с проверкой соответствия бизнес-правилам.|[Master Data Services &#40;проверки&#41;](../master-data-services/validation-master-data-services.md)<br /><br /> [Проверка версии на соответствие бизнес-правилам &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)<br /><br /> [Master Data Services &#40;хранимой процедуры проверки&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)|  
|Создание производных иерархий|Производные иерархии можно обновлять по мере изменения бизнес-потребностей для обеспечения учета всех элементов на соответствующем уровне.|[Производные иерархии &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)<br /><br /> [Создание производной иерархии &#40;Master Data Services&#41;](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|Создание явных иерархий при необходимости|При необходимости использовать иерархии, отличные от многоуровневых, которые включают элементы из одной сущности, можно создавать явные иерархии.|[Явные иерархии &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)<br /><br /> [Создание явной иерархии &#40;Master Data Services&#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|Создание коллекций при необходимости|Если необходимо представить разные группы элементов для отчетов или анализа и не нужно создавать полную иерархию, используются коллекции.<br /><br /> <br /><br /> Примечание. Пользователи могут создавать элементы в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , если у них есть как минимум разрешение на **обновление** объекта модели коллекции и доступ к функциональной области **Обозреватель** .|[&#40;коллекций Master Data Services&#41;](../master-data-services/collections-master-data-services.md)<br /><br /> [Создание Master Data Services &#40;коллекции&#41;](../master-data-services/create-a-collection-master-data-services.md)|  
|Создание определяемых пользователем метаданных|Для описания объектов модели в модель добавляются пользовательские метаданные. Эти метаданные могут включать владельца объекта или источник данных.||  
|Блокировка версии модели и назначение флага версии|Версия модели может блокироваться, чтобы запретить изменять элементы всем пользователям, кроме администраторов. После проверки данных версии на соответствие бизнес-правилам можно зафиксировать версию, чтобы запретить всем пользователям изменять элементы.<br /><br /> Создание и назначение флага версии модели. Флаги помогают пользователям и системам-подписчикам определять используемую версию модели.|[Версии &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)<br /><br /> [Блокировка &#40;версии Master Data Services&#41;](../master-data-services/lock-a-version-master-data-services.md)<br /><br /> [Создание флага версии &#40;Master Data Services&#41;](../master-data-services/create-a-version-flag-master-data-services.md)|  
|Создание представлений подписки|Чтобы системы подписки использовали основные данные, нужно создать представления подписки, которые создают стандартные представления в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .|[Обзор: экспорт &#40;данных Master Data Services&#41;](../master-data-services/overview-exporting-data-master-data-services.md)<br /><br /> [Создание представления подписки для экспорта &#40;данных Master Data Services&#41;](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)|  
|Настройка разрешений для пользователей и групп|Разрешения для пользователей и групп нельзя копировать из тестовой в рабочую среду. Однако тестовую среду можно использовать для определения уровня безопасности, который необходимо будет использовать в производственной среде.|[Master Data Services &#40;безопасности&#41;](../master-data-services/security-master-data-services.md)<br /><br /> [Добавление Master Data Services &#40;группы&#41;](../master-data-services/add-a-group-master-data-services.md)<br /><br /> [Добавление Master Data Services &#40;пользователя&#41;](../master-data-services/add-a-user-master-data-services.md)|  
  
 По окончании можно развернуть модель в рабочей среде с данными или без них. Дополнительные сведения см. в разделе [Развертывание моделей (службы Master Data Services)](../master-data-services/deploying-models-master-data-services.md).  
  
  

