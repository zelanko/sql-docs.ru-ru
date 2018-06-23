---
title: Многоязычные и международные развертывания (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3d485f8-867c-4aa2-a90d-f38fda192534
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f69bea8e13780649203d154f475aca07bdc23acc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098930"
---
# <a name="multi-lingual-and-global-deployments-master-data-services"></a>Многоязычное и международное развертывание (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] поддерживает развертывание компонентов и средств на всех языках, поддерживаемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Local Language Versions in SQL Server](../../sql-server/install/local-language-versions-in-sql-server.md).  
  
## <a name="how-languages-are-used"></a>Использование языков  
 В следующей таблице описывается языковая поддержка для компонентов и средств [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .  
  
|Компонент или средство|Описание|  
|-----------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Программа установки|Выберите программу установки на английском языке, если нужно, чтобы веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] было доступно и поддерживалось на языках, отличных от языка установки. Дополнительные сведения см. в приведенном ниже описании [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .|  
|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]|Язык установки определяет язык [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] . Например, если выбрать в качестве языка установки немецкий, то [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] на этом компьютере будет доступен на немецком языке.|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]|При запуске программы установки на английском языке веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] поддерживается и доступно на всех языках приложения. [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] интерфейс доступен на всех языках приложения, и ввод данных поддерживается на любом языке в зависимости от выбранных языковых параметров клиентского веб-браузера. Если в языковых параметрах задан неподдерживаемый язык приложения, то в службах [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] по умолчанию используется английский.<br /><br /> При выполнении программы установки на любом языке, кроме английского, устанавливаются ресурсы для всех других языков приложения, однако клиенты не могут использовать [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] на языке, отличном от выбранного языка установки. При попытке доступа к [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] на языке, отличном от языка установки, могут возникнуть проблемы с отображением и вводом данных в приложении.|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] базой данных|Данные в базе данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] не относятся к какой-либо конкретной локали. Это позволяет [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] определять способ отображения данных, например дат и чисел, в формате, определяемом языковыми параметрами клиентского веб-браузера.|  
  
## <a name="see-also"></a>См. также  
 [Установка служб Master Data Services](install-master-data-services.md)  
  
  