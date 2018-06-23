---
title: Учебник. Подготовка сервера к репликации | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c9dc9fe91d66158dcba280eb568053f2f0d0c9c5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193085"
---
# <a name="tutorial-preparing-the-server-for-replication"></a>Учебник. Подготовка сервера к репликации
  Перед тем, как настраивать топологию репликации, важно предусмотреть средства безопасности. В этом учебнике описывается, как лучше обезопасить топологию репликации и как настроить распространение, которое является первым шагом в репликации данных. В первую очередь необходимо пройти именно этот учебник.  
  
> [!NOTE]  
>  Чтобы безопасно выполнять репликацию данных между серверами, следует выполнять все рекомендации, приведенные в разделе [Рекомендации по защите репликации](security/replication-security-best-practices.md).  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 В этом учебнике описывается, как подготовить сервер для безопасного выполнения репликации с минимальным числом привилегий. На первом занятии создаются учетные записи службы Windows, используемые для запуска агентов репликации. На втором занятии демонстрируется настройка папки, используемой для формирования и хранения моментальных снимков публикации. На третьем занятии выполняется настройка распространения и установка разрешений.  
  
## <a name="requirements"></a>Требования  
 Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченный опыт работы с репликацией.  
  
 Для работы с этим учебником в системе должны быть установлены следующие компоненты:  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] с базой данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются.  
  
 **Предполагаемое время для выполнения заданий данного учебника: 30 минут.**  
  
## <a name="lessons-in-this-tutorial"></a>Занятия этого учебника  
  
-   [Занятие 1. Создание учетных записей Windows для репликации](lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [Занятие 2. Подготовка папки моментальных снимков](lesson-2-preparing-the-snapshot-folder.md)  
  
-   [Урок 3. Настройка распространения](lesson-3-configuring-distribution.md)  
  
 [Приступить к изучению](lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a>См. также  
 [Настройка распространения](configure-distribution.md)   
 [Безопасность и защита (репликация)](security/security-and-protection-replication.md)  
  
  