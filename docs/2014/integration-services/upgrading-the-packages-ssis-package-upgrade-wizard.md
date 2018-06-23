---
title: Обновление пакетов (мастер обновления пакетов служб SSIS) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.is.upgradewizard.upgradingpackage.f1
ms.assetid: cdb842e3-2e59-4ede-b127-be4fde46875c
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6485982823d1ee2deafa0c981d1fc16950699799
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094597"
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
  
  