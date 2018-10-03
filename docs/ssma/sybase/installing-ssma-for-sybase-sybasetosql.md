---
title: Установка SSMA для SAP ASE (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/29/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8d5a4ce6-b747-46e3-9184-645d56e8b35c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b859c3b9841945241ac0ec9c5238a479a5ba3343
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678952"
---
# <a name="installing-ssma-for-sap-ase-sybasetosql"></a>Установка SSMA для SAP ASE (SybaseToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) для SAP Adaptive Server Enterprise (ASE) состоит из клиентского приложения, используемого для выполнения перехода с SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure. Он также содержит пакет расширения, который поддерживает перенос данных и использование функций системы ASE перенесенных баз данных.  
  
Установите клиентское приложение на компьютер, из которого планируется выполнение действий по миграции. Файлы пакета расширения на компьютере, на котором выполняется установка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны размещаться базы данных после миграции.  
  
## <a name="upgrading-ssma-for-sap-ase"></a>Обновление SSMA для SAP ASE  
Если требуется выполнить обновление до более поздней версии SSMA для SAP ASE, необходимо сначала удалить клиент и пакет расширения server. Затем установите новую версию.  
  
При открытии проекта из более ранней версии SSMA для SAP ASE, SSMA запрашивает, следует ли преобразовать проект до новой версии. Нажмите кнопку **Да** для работы с проектом в более новую версию SSMA.  
  
## <a name="contents"></a>Содержание  
  
|Статья|Описание|  
|---------|---------------|  
|[Установка SSMA для клиентов SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)|Предоставляет сведения и инструкции по установке SSMA для SAP ASE клиента.|  
|[Установка компонентов SSMA в SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)|Содержит сведения и инструкции по установке пакета расширения в экземплярах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Удаление компонентов SAP ASE SSMA для &#40;SybaseToSQL&#41;](../../ssma/sybase/removing-ssma-for-sybase-components-sybasetosql.md)|Предоставляет инструкции по удалению клиента пакет программы и расширение.|  
  
## <a name="see-also"></a>См. также  
[SAP ASE, миграция базы данных в SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
