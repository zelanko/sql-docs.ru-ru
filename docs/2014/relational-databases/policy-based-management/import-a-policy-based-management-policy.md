---
title: Импорт политики управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1f0cecc9489f57512ab9715bdbffdef7d82ece53
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063892"
---
# <a name="import-a-policy-based-management-policy"></a>Импорт политики управления на основе политик
  В этом разделе описывается импорт экземпляра политики управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Импорт экземпляра политики с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставляется с политиками, которые можно использовать для наблюдения за экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию эти политики не устанавливаются в компоненте [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], однако их можно импортировать из места установки по умолчанию — «C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033».  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-import-a-policy-instance"></a>Импорт экземпляра политики  
  
1.  В **обозревателе объектов**щелкните знак "плюс", чтобы развернуть сервер, где будет располагаться импортируемый экземпляр политики.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните правой кнопкой мыши папку **Политики** и выберите команду **Импорт политики**.  
  
5.  Введите имя и путь к файлу в диалоговом окне **Импортировать** либо найдите XML-файл, содержащий политику, при помощи кнопки (**Обзор...** ) и выберите его. Дополнительные сведения о параметрах, доступных в диалоговом окне **Импорт** , см. в разделе [Import Policies Dialog Box](import-policies-dialog-box.md).  
  
6.  После завершения нажмите кнопку **ОК**.  
  
  
