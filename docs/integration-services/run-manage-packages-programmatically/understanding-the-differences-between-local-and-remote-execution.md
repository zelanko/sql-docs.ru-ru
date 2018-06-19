---
title: Основные сведения об отличиях между локальным и удаленным выполнением | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1870f51f50c4104f2092d26b80e54d203b69f75f
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35334058"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a>Основные сведения об отличиях между локальным и удаленным выполнением
  Разработчики пакетов и администраторы должны знать, в чем состоят ограничения, связанные с местом выполнения пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   **Пакет выполняется на том же компьютере, что и запустившая его программа**. Даже если программа загружает пакет, который хранится удаленно на другом сервере, пакет выполняется на локальном компьютере.  
  
-   **Вне среды разработки пакет может выполняться только на том компьютере, на котором установлены службы Integration Services**. Невозможно выполнять пакеты вне среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] на клиентском компьютере, если не установлены службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Условия вашей лицензии на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут не допускать установку служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на дополнительных компьютерах. Службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] являются серверным компонентом и не могут устанавливаться на клиентских компьютерах. Чтобы выполнить пакеты с клиентского компьютера, необходимо запускать их таким способом, который позволяет гарантировать выполнение пакетов на сервере.  
  
 Дополнительные сведения о загрузке и выполнении сохраненного пакета см. в разделах:  
  
-   [Программная загрузка и запуск локального пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [Программная загрузка и запуск удаленного пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 Дополнительные сведения о выполнении пакета и загрузке его выхода в пользовательскую программу см. в разделах:  
  
-   [Загрузка выхода локального пакета](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
## <a name="see-also"></a>См. также:  
 [Программная загрузка и запуск локального пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Программная загрузка и запуск удаленного пакета](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [Загрузка выхода локального пакета](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
