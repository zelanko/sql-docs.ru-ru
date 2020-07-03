---
title: Многоязычные и глобальные развертывания
description: Master Data Services поддерживает развертывание компонентов и средств на всех языках, поддерживаемых SQL Server.
ms.custom: seo-lt-2019
ms.date: 12/13/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: c3d485f8-867c-4aa2-a90d-f38fda192534
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 02cd12f7216e3f73c31be931ab23d47450bcdaaa
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883849"
---
# <a name="multi-lingual-and-global-deployments-master-data-services"></a>Многоязычное и международное развертывание (службы Master Data Services)

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] поддерживает развертывание компонентов и средств на всех языках, поддерживаемых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в статье [Local Language Versions in SQL Server](../../sql-server/install/local-language-versions-in-sql-server.md).  
  
## <a name="how-languages-are-used"></a>Использование языков  
 В следующей таблице описывается языковая поддержка для компонентов и средств [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .  
  
|Компонент или средство|Описание|  
|-----------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Программа установки|Выберите программу установки на английском языке, если нужно, чтобы веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] было доступно и поддерживалось на языках, отличных от языка установки. Дополнительные сведения см. в приведенном ниже описании [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .|  
|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]|Язык установки определяет язык [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] . Например, если выбрать в качестве языка установки немецкий, то [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] на этом компьютере будет доступен на немецком языке.|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]|При запуске программы установки на английском языке веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] поддерживается и доступно на всех языках приложения. [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] интерфейс доступен на всех языках приложения, и ввод данных поддерживается на любом языке в зависимости от выбранных языковых параметров клиентского веб-браузера. Если в языковых параметрах задан неподдерживаемый язык приложения, то в службах [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] по умолчанию используется английский.<br /><br /> При выполнении программы установки на любом языке, кроме английского, устанавливаются ресурсы для всех других языков приложения, однако клиенты не могут использовать [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] на языке, отличном от выбранного языка установки. При попытке доступа к [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] на языке, отличном от языка установки, могут возникнуть проблемы с отображением и вводом данных в приложении.|  
|База данных службы [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|Данные в базе данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] не относятся к какой-либо конкретной локали. Это позволяет [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] определять способ отображения данных, например дат и чисел, в формате, определяемом языковыми параметрами клиентского веб-браузера.|  
  
## <a name="see-also"></a>См. также  
 [Установка служб Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
