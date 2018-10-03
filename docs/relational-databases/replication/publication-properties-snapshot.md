---
title: Свойства публикации, моментальный снимок | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.snapshotformat.f1
ms.assetid: 8e9133b1-fc37-4a85-8a7c-d5eaf172fbef
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fbe678e1cb6e89d366a6f39cc0ab44ee9751e5d9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706661"
---
# <a name="publication-properties-snapshot"></a>Свойства публикаций, моментальный снимок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Страница **Моментальный снимок** диалогового окна **Свойства публикации** позволяет настраивать формат моментальных снимков, указывать месторасположение папки моментальных снимков и скрипты, исполняемые до и после выполнения приложения моментальных снимков. Папка моментальных снимков должна быть в общем доступе и иметь достаточные разрешения для чтения и записи в нее файлов агентами. Дополнительные сведения о надлежащей защите папок см. в статье [Организация безопасности папки моментальных снимков](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
> [!NOTE]  
>  Изменения требуют новый моментальный снимок для публикации. Дополнительные сведения см. в статье [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
## <a name="options"></a>Параметры  
 **Формат моментального снимка**  
 Выберите для формата моментальных снимков собственный или символьный режим.  
  
-   Выберите **Собственный SQL Server — все подписчики должны быть серверами SQL Server** , если все подписчики являются экземплярами [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не относящимися к [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Собственный формат моментальных снимков обеспечивает максимальную производительность.  
  
-   Выберите **Символьный — необходим в том случае, если на стороне издателя или подписчике не используется SQL Server** , если любой из подписчиков использует [!INCLUDE[ssEW](../../includes/ssew-md.md)] или является подписчиком, отличным от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Местоположение файлов моментальных снимков**  
 Выберите местоположение для хранения файлов моментальных снимков. Их можно сохранять в расположении по умолчанию; а также в другом месте, как наряду с местом хранения по умолчанию, так и вместо него. Файлы, хранимые в альтернативном месте хранения, можно сжимать.  
  
-   Выберите **Поместить файлы в папку по умолчанию** , чтобы использовать папку по умолчанию для моментальных снимков издателя. В этом диалоговом окне расположение папки моментальных снимков доступно только для чтения, потому что его можно изменить только для издателя в диалоговом окне **Свойства распространителя** . Дополнительные сведения см. в статье [Определение расположения моментальных снимков по умолчанию (SQL Server Management Studio)](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md).  
  
-   Выберите **Поместить файлы в следующую папку** , чтобы указать другое местоположение файла вместе с его расположением по умолчанию или вместо него. Введите путь в текстовое поле или нажмите **Обзор** для выбора местоположения. Выберите **Выполнять сжатие файлов моментальных снимков в этой папке** , чтобы сжимать файлы в альтернативном местоположении. Альтернативное местоположение может находиться на другом сервере, на сетевом диске, на съемном носителе (например на компакт-диске или съемном диске). Дополнительные сведения см. в разделах [Alternate Snapshot Folder Locations](../../relational-databases/replication/alternate-snapshot-folder-locations.md) и [Compressed Snapshots](../../relational-databases/replication/compressed-snapshots.md).  
  
 **Выполнить дополнительные скрипты**  
 Укажите скрипты, которые необходимо выполнить до и после применения моментального снимка на сервере подписчика. Нельзя указывать скрипты, если **Формат моментального снимка** **Символьный**.  
  
 Скрипты являются необязательными, они позволяют легко выполнять команды и применять административные изменения на серверах подписчиков. Дополнительные сведения о выполнении скриптов см. в статье [Выполнение скриптов до и после применения моментального снимка](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Введите путь в текстовое поле **Перед применением моментального снимка выполните этот скрипт** или нажмите кнопку **Обзор** для указания пути к скрипту.  
  
-   Введите путь в текстовое поле **После применения моментального снимка выполнить этот скрипт:** или нажмите кнопку **Обзор** для указания пути к скрипту.  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Создание и применение исходного моментального снимка](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)   
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
