---
title: Перенос точки управления служебной программой из одного экземпляра SQL Server на другой (служебная программа SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b402fd9e-0bea-4c38-a371-6ed7fea12e96
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b4518884b3fe17ea3a638ed21210775af7c4921c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2020
ms.locfileid: "62640337"
---
# <a name="move-a-ucp-from-one-instance-of-sql-server-to-another-sql-server-utility"></a>Перенос точки управления служебной программой из одного экземпляра SQL Server на другой (служебная программа SQL Server)
  В этом разделе описано, как переместить точку управления служебной программой с одного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на другой в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="move-a-ucp-from-one-instance-of-sql-server-to-another"></a>Перемещение пункта управления программой с одного экземпляра SQL Server на другой.  
  
1.  Создайте новый пункт управления программой на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на который будет перемещен исходный пункт управления программой. Дополнительные сведения см. в статье [Создание точки управления служебной программой SQL Server (служебная программа SQL Server Utility)](create-a-sql-server-utility-control-point-sql-server-utility.md).  
  
2.  При наличии в программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] настроек, отличных от параметров по умолчанию, для любых экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запишите пороговые значения политик, чтобы их можно было вновь задать на новом пункте управления программой. Политики по умолчанию применяются при добавлении экземпляров в новый пункт управления программой. Если на данный экземпляр распространяется действие политик по умолчанию, то в столбце [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Тип политики **списка программы** Utility отображается значение **Глобальная** .  
  
3.  Удалите все управляемые экземпляры из старого пункта управления программой. Дополнительные сведения см. в разделе [Удаление экземпляра SQL Server из служебной программы SQL Server](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
4.  Создайте резервную копию хранилища данных управления программой (UMDW) старого пункта управления программой. Имя файла — Sysutility_mdw_\<GUID>_DATA, а местоположение базы данных по умолчанию — \<Системный диск>:\Program Files\Microsoft SQL Server\MSSQL10_50.<Имя_пункта_управления_программой>\MSSQL\Data\\, где \<Системный диск> обычно указывает на диск C:\. Дополнительные сведения см. в статье [Копирование баз данных путем создания и восстановления резервных копий](../databases/copy-databases-with-backup-and-restore.md).  
  
5.  Восстановите резервную копию UMDW на новый пункт управления программой. Дополнительные сведения см. в статье [Копирование баз данных путем создания и восстановления резервных копий](../databases/copy-databases-with-backup-and-restore.md).  
  
6.  Зарегистрируйте экземпляры в новом пункте управления программой, чтобы они попали под управление программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Регистрация экземпляра SQL Server (служебная программа SQL Server Utility)](enroll-an-instance-of-sql-server-sql-server-utility.md).  
  
7.  Задайте требуемые пользовательские определения политик для экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
8.  Подождите завершения операций сбора и статической обработки данных в течение примерно одного часа.  
  
9. Чтобы обновить данные, щелкните правой кнопкой мыши узел **Управляемые экземпляры** в **Обозревателе программы**и выберите команду **Обновить**. Данные в списке отображаются на панели содержимого **Обозревателя программы** . Дополнительные сведения см. в статье [Просмотр результатов политики исправности ресурсов (служебная программа SQL Server)](view-resource-health-policy-results-sql-server-utility.md).  
  
## <a name="see-also"></a>См. также:  
 [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md)   
 [Регистрация экземпляра SQL Server (служебная программа SQL Server)](enroll-an-instance-of-sql-server-sql-server-utility.md)  
  
  
