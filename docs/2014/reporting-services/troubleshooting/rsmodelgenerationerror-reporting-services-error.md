---
title: rsModelGenerationError — ошибка служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5a64511c7c44a4fed583c8276b2b4abaff01ee51
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56021935"
---
# <a name="rsmodelgenerationerror---reporting-services-error"></a>rsModelGenerationError - Ошибка службы Reporting Services
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|rsRenderingError|  
|Источник события|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Компонент|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Текст сообщения|Во время построения модели произошла ошибка. (rsModelGenerationError) (ReportingServicesLibrary) %1|  
  
## <a name="explanation"></a>Объяснение  
 Невозможно сформировать модель отчета. В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 с пакетом обновления 1 (SP1) и ранее эта ошибка обычно происходит в том случае, если объекту System.Data.DataSet не удается обработать таблицу или связь в схеме базы данных, например когда для одного и того же столбца таблицы определены два внешних ключа.  
  
## <a name="user-action"></a>Действие пользователя  
 Для определения причины ошибки просмотрите файлы журналов сервера отчетов, расположенные в папке \Microsoft SQL Server\\<SQL Server Instance\>\Reporting Services\LogFiles.  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
