---
title: Импорт политики управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 54e0ca12595b0ce8bdde128c9261918c910ffdcf
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934353"
---
# <a name="import-a-policy-based-management-policy"></a>Импорт политики управления на основе политик
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В этом разделе описывается импорт экземпляра политики управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Разрешения
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.

  
##  <a name="using-sql-server-management-studio"></a>Использование среды SQL Server Management Studio  
  
### <a name="to-import-a-policy-instance"></a>Импорт экземпляра политики  
  
1.  В **обозревателе объектов**щелкните знак "плюс", чтобы развернуть сервер, где будет располагаться импортируемый экземпляр политики.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните правой кнопкой мыши папку **Политики** и выберите команду **Импорт политики**.  
  
5.  Введите имя и путь к файлу в диалоговом окне **Импортировать** либо найдите XML-файл, содержащий политику, при помощи кнопки (**Обзор...**) и выберите его. Дополнительные сведения о параметрах, доступных в диалоговом окне **Импорт** , см. в разделе [Import Policies Dialog Box](../../relational-databases/policy-based-management/import-policies-dialog-box.md).  
  
6.  После завершения нажмите кнопку **ОК**.  


## <a name="example-policies"></a>Примеры политик
 Примеры политик не включены в [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], однако доступ к ранее распространявшимся примерам политик можно получить, установив [SQL Server Management Studio 17](../../ssms/release-notes-ssms.md#previous-ssms-releases).  После установки SQL Server Management Studio 17 примеры политик можно найти в `C:\Program Files (x86)\Microsoft SQL Server\140\Tools\Policies`. Эти политики можно импортировать и использовать в качестве основы для собственных политик управления на основе политик.
