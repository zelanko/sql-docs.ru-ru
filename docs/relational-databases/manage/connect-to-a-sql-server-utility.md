---
title: Подключение к служебной программе SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1be0f1b4a9aa114c6c0d630be5919b5f519ff6a2
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033335"
---
# <a name="connect-to-a-sql-server-utility"></a>Подключение к служебной программе SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Перед подключением к программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо создать точку управления служебной программой. Дополнительные сведения см. в разделе [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
 Для просмотра работоспособности ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и управления ей подключитесь к программе [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с помощью среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSMS).  
  
 Подключение к программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды SSMS.  
  
1.  Запустите среду SSMS.  
  
2.  В среде SSMS подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  В меню **Вид** выберите пункт **Обозреватель служебных программ**.  
  
4.  На панели навигации обозревателя служебных программы щелкните ![](../../relational-databases/manage/media/connect-to-utility.gif "Connect_to_Utility")**Соединение со служебной программой**.  
  
5.  В диалоговом окне **Подключение к серверу** укажите имя экземпляра точки управления служебной программой (UCP) и нажмите кнопку **Подключить**.  
  
6.  Откройте панель навигации обозревателя программы, чтобы отобразить дерево ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , зарегистрированных в этом пункте управления программой.  
  
 При создании новой точкой управления служебной программой также устанавливается соединение со служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Создание точки управления служебной программой SQL Server (служебная программа SQL Server Utility)](../../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md).  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Просмотр результатов политики исправности ресурсов (служебная программа SQL Server)](../../relational-databases/manage/view-resource-health-policy-results-sql-server-utility.md)  
  
  
