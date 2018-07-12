---
title: Обновление пакетов (мастер обновления пакетов служб SSIS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.is.upgradewizard.upgradingpackage.f1
ms.assetid: cdb842e3-2e59-4ede-b127-be4fde46875c
caps.latest.revision: 15
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b06d9a0b4fd8b365e327d77f776bd75781e8128c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158595"
---
# <a name="upgrading-the-packages-ssis-package-upgrade-wizard"></a>Обновление пакетов (мастер обновления пакетов служб SSIS)
  Страница **Обновление пакетов** используется для слежения за ходом обновления пакетов и прерывания процесса обновления. Мастер обновления пакетов служб [!INCLUDE[ssIS](../includes/ssis-md.md)] обновляет выбранные пакеты один за другим.  
  
 **Просмотр обновленных пакетов, сохраненных в базе данных SQL Server или в хранилище пакетов**  
  
-   В обозревателе объектов среды [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]установите соединение с локальным экземпляром служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], а затем разверните узел **Сохраненные пакеты** , чтобы увидеть обновленные пакеты.  
  
 **Просмотр обновленных пакетов, которые были обновлены из SQL Server Data Tools**  
  
-   В обозревателе решений среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , а затем разверните узел **Пакеты служб SSIS** , чтобы увидеть обновленные пакеты.  
  
## <a name="options"></a>Параметры  
 **Панель сообщений**  
 Отображает сообщения о ходе обновления и сводку в течение процесса обновления.  
  
 **Действие**  
 Просмотр действий по обновлению.  
  
 **Состояние**  
 Просмотр результатов каждого действия.  
  
 **Сообщение**  
 Просмотр сообщений об ошибках, которые формируются каждым действием.  
  
 **Остановить**  
 Остановка обновления пакетов.  
  
 **Отчет**  
 Выбор действий с отчетом, содержащим результаты обновления пакетов:  
  
-   просмотр отчета в режиме в сети;  
  
-   сохранение отчета в файл;  
  
-   копирование отчета в буфер обмена;  
  
-   отправка отчета по электронной почте.  
  
## <a name="see-also"></a>См. также  
 [Обновление пакетов служб Integration Services](install-windows/upgrade-integration-services-packages.md)  
  
  
