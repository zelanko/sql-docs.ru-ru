---
title: Установка SSMA для SAP ASE (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 11/29/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: a904a7f17d90449406bef18f7f74022cf2fe049a
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779000"
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Установка SSMA для SAP ASE (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) для SAP адаптивной Server Enterprise (ASE) состоит из клиентского приложения, который позволяет выполнить миграцию с SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. Он также содержит пакет расширения, который поддерживает перенос данных и использование системных функций ASE перенесенных баз данных.  
  
Установите клиентское приложение на компьютере, с которого планируется выполнить действия по миграции. Установите расширение файлы пакета на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на котором должны быть размещены базы данных после миграции.  
  
## <a name="upgrading-ssma-for-sap-ase"></a>Обновление SSMA для SAP ASE  
Если требуется выполнить обновление до более поздней версии SSMA для SAP ASE, необходимо сначала удалить клиент и пакет расширения сервера. Установите более новую версию.  
  
При открытии проекта из более ранней версии SSMA для SAP ASE SSMA запрашивает необходимо преобразовать проект до новой версии. Нажмите кнопку **Да** для работы с проектом в новой версии SSMA.  
  
## <a name="contents"></a>Содержание  
  
|Статья|Описание|  
|---------|---------------|  
|[Установка SSMA для клиентов SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Предоставляет сведения и инструкции по установке SSMA для SAP ASE клиента.|  
|[Установка компонентов SSMA на SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Сведения и инструкции по установке пакета расширения в экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Удаление SSMA для компонентов SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Содержит инструкции по удалению клиента пакет программы и расширение.|  
  
## <a name="see-also"></a>См. также  
[Перенос SAP ASE баз данных SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
