---
title: Развертывание решений модели с использованием XML для Аналитики | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- XML scripts [Analysis Services]
- scripts [Analysis Services], deployment
- deploying [Analysis Services], XML scripts
- Analysis Services deployments, XML scripts
ms.assetid: a8cb1837-fcac-4730-bea4-a72cf94d9f7c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 68700aaba6c335bf7fe9686961933eac5c52f8f7
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66075370"
---
# <a name="deploy-model-solutions-using-xmla"></a>Развертывание решений модели с помощью XMLA
  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]параметр **Используя CREATE** команды **Создать скрипт для базы данных** создает XML-скрипт всей базы данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или одного из составляющих ее объектов. Получившийся в результате скрипт затем можно запускать на другом компьютере для повторного создания схемы (метаданных) базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Скрипт формирует всю базу данных, а механизм добавочного обновления уже развернутых объектов при использовании скрипта отсутствует. После выполнения скрипта и развертывания базы данных вновь созданную базу необходимо обработать до ее просмотра пользователями.  
  
 Дополнительные сведения о команде **Создать скрипт для базы данных** см. в разделе [Документирование и работа со скриптами в базе данных служб Analysis Services](document-and-script-an-analysis-services-database.md).  
  
## <a name="modifying-object-properties-in-the-xml-script"></a>Изменение свойств объектов в XML-скрипте  
 При использовании команды **Создать скрипт для базы данных** нельзя изменять определенные свойства (например, имя базы данных, строки соединений с источниками данных и параметры безопасности) объектов базы данных. Эти свойства необходимо либо изменить вручную в скрипте после его формирования, либо изменить в развернутой базе данных после выполнения скрипта.  
  
> [!IMPORTANT]  
>  XML-скрипт не будет содержать пароль, если он указан в строке соединения для источника данных или для олицетворения. Поскольку в данном скрипте пароль требуется для обработки, его нужно добавить вручную в скрипт перед запуском либо добавить в XML после выполнения скрипта.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решений модели с использованием мастера развертывания](deploy-model-solutions-using-the-deployment-wizard.md)   
 [Синхронизация баз данных служб Analysis Services](synchronize-analysis-services-databases.md)  
  
  
