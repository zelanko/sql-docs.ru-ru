---
title: Скрипт развертывания экземпляра CDC | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ad6efe1291adffd73769f8f6f4defa28abe8fbef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67968291"
---
# <a name="cdc-instance-deployment-script"></a>Скрипт развертывания экземпляра CDC

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Диалоговое окно «Скрипт развертывания экземпляра CDC», в котором отображается скрипт развертывания экземпляра CDC. С помощью этого скрипта можно воссоздавать базу данных CDC со всеми ее артефактами на другом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 После выполнения скрипта развертывания необходимо проверить следующее.  
  
-   Скрипт развертывания предполагает, что целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был подготовлен для CDC в консоли настройки службы CDC Oracle или с помощью **скрипта подготовки** , сформированный этой программой.  
  
-   Часть скрипта, которая используется для обеспечения работы CDC в базе данных, должен запускать `sysadmin`.  
  
-   Скрипт не сохраняет пароль Oracle для интеллектуального анализа журнала. Его необходимо задать вручную после завершения работы скрипта и запуска службы CDC Oracle.  
  
 В диалоговом окне **Скрипт развертывания экземпляра CDC** выберите следующие параметры.  
  
 **Сохранить как**  
 Сохранение скрипта в текстовый файл, который можно разместить в любом каталоге. Файл со скриптом можно скопировать на любой другой сервер, чтобы выполнить его там.  
  
 **Копировать**  
 Копирует скрипт в буфер обмена. Затем скрипт можно будет вставить в среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или любой текстовый редактор для последующего выполнения.  
  
## <a name="see-also"></a>См. также:  
 [Подготовка SQL Server для CDC](../../integration-services/change-data-capture/prepare-sql-server-for-cdc.md)  
  
  
