---
title: Повторное развертывание пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- redeploying packages [Integration Services]
- deploying packages [Integration Services], redeploying
ms.assetid: 86806efb-8cf4-4f9d-9824-1152cb4c495c
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 33eb116ec2824af31eae236a8efd4038a9cbbb68
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84964584"
---
# <a name="redeployment-of-packages"></a>Повторное развертывание пакетов
  После развертывания проекта может понадобится обновить или расширить функциональные возможности пакета и затем повторно развернуть проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий обновленные пакеты. В рамках процесса повторного развертывания пакетов необходимо просмотреть свойства конфигурации, включенные в программу развертывания. Например, можно запретить изменение конфигурации после повторного развертывания пакета.  
  
## <a name="process-for-redeployment"></a>Процесс повторного развертывания  
 После завершения обновления пакетов перестраивается проект, папка развертывания копируется на целевой компьютер и затем повторно запускается мастер установки пакета.  
  
 При обновлении нескольких пакетов в проекте развертывание всего пакета может не понадобиться. Для развертывания только нескольких пакетов можно создать новый проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , добавить обновленные пакеты в новый проект, затем скомпоновать и развернуть проект. Конфигурации пакетов автоматически копируются с пакетом при добавлении пакета в другой проект.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [Развертывание пакетов с помощью программы развертывания](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)  
  
  
