---
title: Изменение учетной записи-посредника для набора элементов сбора служебной программы на Управляемый экземпляр SQL Server (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ff37ba8b-a08c-4109-b6e2-5748c995a52c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: efa4af0c12379abaab2d810fd39ce6d7a3b0afef
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62806328"
---
# <a name="change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server-sql-server-utility"></a>Изменение учетной записи-посредника для набора элементов сбора служебной программы на управляемом экземпляре SQL Server (служебная программа SQL Server)
  В этом разделе описано, как изменить учетную запись-посредник для набора элементов сбора служебной программы на управляемом экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-change-the-proxy-account-for-the-utility-collection-set-on-a-managed-instance-of-sql-server"></a>Изменение учетной записи-посредника для набора элементов сбора служебной программы на управляемом экземпляре SQL Server  
  
1.  Удалите управляемый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из программы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   В **Обозревателе программ** среды SSMS щелкните узел **Управляемые экземпляры** .  
  
    -   В списке **обозревателя программ** щелкните правой кнопкой мыши имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выберите команду **Удалить управляемый экземпляр…** . Дополнительные сведения см. в разделе [Удаление экземпляра SQL Server из служебной программы SQL Server](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
2.  Снова зарегистрируйте экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   В **обозревателе программ** среды SSMS щелкните правой кнопкой мыши узел **Управляемые экземпляры** и выберите команду **Добавить управляемый экземпляр…** .  
  
    -   Выполните предлагаемые мастером действия, указав новую учетную запись-посредник.  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md)   
 [Устранение неполадок служебной программы SQL Server](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
