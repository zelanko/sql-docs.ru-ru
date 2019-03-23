---
title: Добавление или удаление проекта служб Integration Services в решении | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- Integration Services projects, adding
- SQL Server Integration Services projects, adding
- SSIS projects, adding
- projects [Integration Services], adding
ms.assetid: f01f6475-b63c-41dc-82ac-b62162b3adf7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2581aaffaeeba033e92cff305f0e9904cfb9a970
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385523"
---
# <a name="add-or-remove-an-integration-services-project-in-a-solution"></a>Добавление или удаление проектом служб Integration Services из решения
  Следующие процедуры описывают способы добавления или удаления проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в решении.  
  
 Добавлять проекты к существующему решению и удалять их из него можно только тогда, когда решение отображается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Если выбрать в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] параметр **Всегда показывать решение**, среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] будет отображать решение, даже когда в нем всего один проект. В противном случае среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] будет отображать решение, только когда в нем более одного проекта. Дополнительными могут быть проекты служб [!INCLUDE[ssIS](../includes/ssis-md.md)] или проекты других типов.  
  
## <a name="adding-an-integration-services-project"></a>Добавление проекта служб Integration Services  
 При добавлении проекта можно создать новый пустой проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] или добавить проект, созданный для другого решения. Добавить проект к существующему решению можно, только если решение отображается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
#### <a name="to-add-a-new-integration-services-project-to-a-solution"></a>Добавление нового проекта служб Integration Services к решению  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте решение, к которому нужно добавить новый проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , и выполните одно из следующих действий:  
  
    -   Щелкните решение правой кнопкой, выберите пункт **Добавить**, а затем **Новый проект**.  
  
    -   В меню **Файл** выберите пункт **Добавить**, затем щелкните **Создание проекта**.  
  
2.  В диалоговом окне **Добавить новый проект** щелкните **Проект служб Integration Services** на панели **Шаблоны** .  
  
3.  Дополнительно можно изменить имя и расположение проекта.  
  
4.  Нажмите кнопку **ОК**.  
  
#### <a name="to-add-an-existing-integration-services-project-to-a-solution"></a>Добавление существующего проекта служб Integration Services к решению  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте решение, к которому нужно добавить существующий проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , и выполните одно из следующих действий:  
  
    -   Щелкните решение правой кнопкой мыши, выберите **Добавить**, а затем щелкните **Существующий проект**.  
  
    -   В меню **Файл** выберите **Добавить**, а затем — **Существующий проект**.  
  
2.  В диалоговом окне **Добавление существующего проекта** выберите локальный проект, который нужно добавить, и щелкните **Открыть**.  
  
3.  Проект будет добавлен в папку решений **Обозревателя решений**.  
  
## <a name="removing-an-integration-services-project"></a>Удаление проекта служб Integration Services  
 Удалить проект из решения можно, только если решение отображается в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. После отображения решения можно удалить все проекты, кроме одного. Когда остается только один проект, среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] больше не отображает папку решения и удалить последний проект становится невозможным.  
  
#### <a name="to-remove-an-integration-services-project-from-a-solution"></a>Удаление проекта служб Integration Services из решения  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]нужно открыть решение, из которого необходимо удалить проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  В обозревателе решений щелкните правой кнопкой мыши проект и выберите команду **Выгрузить проект**.  
  
3.  Чтобы подтвердить удаление, нажмите кнопку **ОК** .  
  
## <a name="see-also"></a>См. также  
 [Службы Integration Services &#40;SSIS&#41; проектов](integration-services-ssis-projects-and-solutions.md)   
 [Создание нового проекта служб Integration Services](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
  
