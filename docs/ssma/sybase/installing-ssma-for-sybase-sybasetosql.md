---
title: "Установка SSMA для SAP ASE (SybaseToSQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 759a7084024e1c608431683de6dae5a6fb40304e
ms.openlocfilehash: 7b2c96006c5495c89486c8a86e1b60b64f2dd22c
ms.contentlocale: ru-ru
ms.lasthandoff: 10/03/2017

---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Установка SSMA для SAP ASE (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) для SAP ASE состоит из клиентского приложения, который позволяет выполнить миграцию из SAP адаптивной Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. Он также содержит пакет расширения, который поддерживает перенос данных и использование системных функций ASE перенесенных баз данных.  
  
Для установки клиентского приложения на компьютере, в котором будет выполнять действия по миграции. Необходимо установить файлы пакета расширения на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для размещения базы данных после миграции.  
  
## <a name="upgrading-ssma-for-sybase"></a>Обновление SSMA для СУБД Sybase  
Если требуется выполнить обновление до более поздней версии SSMA для SAP ASE, необходимо сначала удалить клиента и пакет расширения сервера, а затем установить новую версию.  
  
При открытии проекта из более ранней версии SSMA для SAP ASE SSMA запрашивает необходимо преобразовать проект до новой версии. Необходимо нажать кнопку **Да** для работы с проектом в новой версии SSMA.  
  
## <a name="contents"></a>Содержание  
  
|Раздел|Description|  
|---------|---------------|  
|[Установка SSMA для клиентов SAP ASE &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Предоставляет сведения и инструкции по установке клиента SSMA.|  
|[Установка компонентов SSMA на SQL Server &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Сведения и инструкции по установке пакета расширения в экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Удаление SSMA для компонентов SAP ASE &#40; SybaseToSQL &#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Содержит инструкции по удалению клиента пакет программы и расширение.|  
  
## <a name="see-also"></a>См. также:  
[Миграция SAP ASE баз данных в SQL Server — база данных SQL Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  

