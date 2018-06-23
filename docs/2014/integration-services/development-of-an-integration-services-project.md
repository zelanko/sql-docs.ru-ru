---
title: Разработка служб Integration Services проекта | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Integration Services], creating
- Integration Services projects, creating
- SQL Server Integration Services projects, creating
- SSIS projects, creating
ms.assetid: 6e90b016-36a5-415e-9440-a20199fffff0
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2eab6834047938a908cc9ca034ad64ad8c7082cc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096695"
---
# <a name="development-of-an-integration-services-project"></a>Разработка проекта служб Integration Services
  Добавление пакетов [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] осуществляется в проекты. Для создания проектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и работы с ними необходимо установить среду [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] . Дополнительные сведения см. в статье [Установка служб Integration Services](install-windows/install-integration-services.md).  
  
 При создании нового проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]отображается диалоговое окно **Создание проекта** с шаблоном **Проект служб Integration Services** . Этот шаблон позволяет создать проект, в котором содержится единственный пакет.  
  
## <a name="projects-and-solutions"></a>Проекты и решения  
 Проекты сохраняются в решениях. Можно сначала создать решение, затем добавить к решению проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Если не существует никаких решений, среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] автоматически создает для пользователя решение после того, как пользователь сначала создаст проект. Решение может содержать несколько проектов различного типа.  
  
> [!NOTE]  
>  По умолчанию при создании нового проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]решение на панели **Обозреватель решений** не отображается. Чтобы изменить это поведение по умолчанию, в меню **Сервис** выберите пункт **Параметры**. В диалоговом окне **Параметры** последовательно раскройте элементы **Проекты и решения**, а затем щелкните **Общие**. На странице **Общие** выберите **Всегда показывать решение**.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Создание нового проекта служб Integration Services](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
-   [Добавление элемента к проекту служб Integration Services](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)  
  
-   [Добавление или удаление проектом служб Integration Services из решения](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  