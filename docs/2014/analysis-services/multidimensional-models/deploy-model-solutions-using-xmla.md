---
title: Развертывание решений модели с использованием XML для Аналитики | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML scripts [Analysis Services]
- scripts [Analysis Services], deployment
- deploying [Analysis Services], XML scripts
- Analysis Services deployments, XML scripts
ms.assetid: a8cb1837-fcac-4730-bea4-a72cf94d9f7c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 872f4297aa6d98c35b85bb81588c27d1060066fd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102112"
---
# <a name="deploy-model-solutions-using-xmla"></a>Развертывание решений модели с помощью XMLA
  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]параметр **Используя CREATE** команды **Создать скрипт для базы данных** создает XML-скрипт всей базы данных служб [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или одного из составляющих ее объектов. Получившийся в результате скрипт затем можно запускать на другом компьютере для повторного создания схемы (метаданных) базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Скрипт формирует всю базу данных, а механизм добавочного обновления уже развернутых объектов при использовании скрипта отсутствует. После выполнения скрипта и развертывания базы данных вновь созданную базу необходимо обработать до ее просмотра пользователями.  
  
 Дополнительные сведения о команде **Создать скрипт для базы данных** см. в разделе [Документирование и работа со скриптами в базе данных служб Analysis Services](document-and-script-an-analysis-services-database.md).  
  
## <a name="modifying-object-properties-in-the-xml-script"></a>Изменение свойств объектов в XML-скрипте  
 При использовании команды **Создать скрипт для базы данных** нельзя изменять определенные свойства (например, имя базы данных, строки соединений с источниками данных и параметры безопасности) объектов базы данных. Эти свойства необходимо либо изменить вручную в скрипте после его формирования, либо изменить в развернутой базе данных после выполнения скрипта.  
  
> [!IMPORTANT]  
>  XML-скрипт не будет содержать пароль, если он указан в строке соединения для источника данных или для олицетворения. Поскольку в данном скрипте пароль требуется для обработки, его нужно добавить вручную в скрипт перед запуском либо добавить в XML после выполнения скрипта.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решений модели с помощью мастера развертывания](deploy-model-solutions-using-the-deployment-wizard.md)   
 [Синхронизация баз данных служб Analysis Services](synchronize-analysis-services-databases.md)  
  
  