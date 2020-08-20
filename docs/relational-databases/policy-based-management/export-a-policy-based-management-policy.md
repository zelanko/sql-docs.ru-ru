---
description: Экспорт политики управления на основе политик
title: Экспорт политики управления на основе политик | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, export policy
ms.assetid: f0001b33-9078-4432-8460-496736fb325a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 62fff3bda286f50b2220dbb1ea4732547e98829f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494027"
---
# <a name="export-a-policy-based-management-policy"></a>Экспорт политики управления на основе политик
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В этом разделе описывается экспорт политики управления на основе политик в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Экспорт политики с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Требуется членство в роли PolicyAdministratorRole базы данных msdb.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-export-a-policy"></a>Экспорт политики  
  
1.  В обозревателе объектов щелкните знак «плюс», чтобы развернуть сервер, содержащий политику управления на основе политик, которую необходимо экспортировать.  
  
2.  Щелкните знак «плюс», чтобы развернуть папку **Управление** .  
  
3.  Щелкните знак «плюс», чтобы развернуть папку **Управление политиками**.  
  
4.  Щелкните знак «плюс», чтобы развернуть папку **Политики** .  
  
5.  Щелкните правой кнопкой мыши политику, которую необходимо экспортировать, а затем выберите пункт **Экспортировать политику**.  
  
6.  В диалоговом окне **Экспорт политики** введите в адресной строке имя файла и путь к нему. Также можно найти подходящее расположение для файла в области панели навигации диалогового окна, а затем ввести имя XML-файла в поле **Имя файла** .  
  
7.  По завершении щелкните **Сохранить**.  

