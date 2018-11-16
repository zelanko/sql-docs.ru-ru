---
title: Критические изменения в функциях ядра СУБД в SQL Server 2017 | Документы Майкрософт
description: Критические изменения в функциях ядра СУБД в SQL Server 2017
ms.date: 04/19/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.custom: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- breaking changes 2017 [SQL Server]
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 5161f81aac7496f5bf674c8fcbf1fda6063c158f
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350408"
---
# <a name="breaking-changes-to-database-engine-features-in-includesssqlv14-mdincludessssqlv14-mdmd"></a>Критические изменения в функциях ядра СУБД в [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)]
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


  В этом разделе описываются критические изменения в [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)]. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При обновлении могут возникнуть следующие проблемы.  
  
## <a name="breaking-changes-in-includesssqlv14-mdincludessssqlv14-mdmdincludessdeincludesssde-mdmd"></a>Критические изменения в [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)]  
  
-  Среда CLR использует управление доступом для кода (CAS) в .NET Framework, которое больше не поддерживается в качестве границы безопасности. Начиная с [!INCLUDE[sssqlv14-md](../includes/sssqlv14-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)], появился параметр `sp_configure`, называемый `clr strict security`, для повышения безопасности сборок среды CLR. Параметр clr strict security включен по умолчанию и рассматривает сборки `SAFE` и `EXTERNAL_ACCESS`, как если бы они были помечены `UNSAFE`. Параметр `clr strict security` можно отключить для обеспечения обратной совместимости, но это делать не рекомендуется. Если параметр `clr strict security` отключен, сборки среды CLR, созданные с помощью `PERMISSION_SET = SAFE`, могут получать доступ к внешним системным ресурсам, вызывать неуправляемый код и получать права **sysadmin**. После включения строгой безопасности сборки без подписи загружаться не будут. Кроме того, если в базе данных есть сборки `SAFE` или `EXTERNAL_ACCESS` сборки либо можно выполнить инструкции `RESTORE` или `ATTACH DATABASE`, могут возникать ошибки загрузки сборок.   
  Для загрузки сборок необходимо изменить или повторно создать каждую сборку, чтобы она была подписана сертификатом или асимметричным ключом, имеющим соответствующее имя входа с разрешением `UNSAFE ASSEMBLY` на сервере. Дополнительные сведения см. в статье о параметре [clr strict security](../database-engine/configure-windows/clr-strict-security.md). 


  
## <a name="previous-versions"></a>Предыдущие версии  

-   [Критические изменения в функциях ядра СУБД в SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md)  
  
-   [Критические изменения в функциях компонента ядра СУБД в SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md)  
  
-   [Критические изменения в функциях компонента ядра СУБД в SQL Server 2012](breaking-changes-to-database-engine-features-in-sql-server-2016.md)  
  
-   [Критические изменения в функциях компонента ядра СУБД в SQL Server 2008](breaking-changes-to-database-engine-features-in-sql-server-2016.md)  
  
## <a name="see-also"></a>См. также:  
 [Устаревшие функции ядра СУБД в SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Неподдерживаемые функции ядра СУБД в SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Обратная совместимость компонента ядра СУБД SQL Server](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Уровень совместимости инструкции ALTER DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  
