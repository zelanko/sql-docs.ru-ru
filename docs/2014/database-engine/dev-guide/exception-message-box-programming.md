---
title: Сообщение об исключении программирование окон | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ExceptionMessageBox class, about ExceptionMessageBox class
- exception message box [SQL Server], about exception message box
- exception message box [SQL Server]
- interfaces [SQL Server]
- exceptions [SQL Server]
- messages [SQL Server], exception message box
ms.assetid: 0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0adef635d88a05925da924c4bab396f1da58e530
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100909"
---
# <a name="exception-message-box-programming"></a>Программирование окон сообщений об исключениях
  Окно сообщения об исключении представляет собой программный интерфейс, который устанавливается и используется [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] графическими компонентами. Окно сообщения об исключении является поддерживаемой управляемой сборкой, которая используется в приложении, чтобы обеспечить в приложении более полное управление сообщениями и дать пользователям возможность сохранять содержимое сообщения об ошибке для последующего просмотра сообщений и получения помощи при работе с ними. Поскольку окно сообщения об исключении устанавливается всеми выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], за исключением [!INCLUDE[ssEW](../../includes/ssew-md.md)], его можно использовать без дополнительной настройки на любом компьютере, на котором установлены клиентские компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Класс <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> в пространстве имен <xref:Microsoft.SqlServer.MessageBox> имеет все возможности класса <xref:System.Windows.Forms.MessageBox> и некоторые дополнительные. Класс <xref:System.Windows.Forms.MessageBox> идеально подходит для всех задач, в которых используется класс <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>, он разработан для эффективного управления исключениями управляемого кода. Окно сообщения об исключении выполняет следующие действия.  
  
-   Обеспечивает настраиваемый текст для кнопок (не более пяти). Кнопки и диалоговые окна автоматически меняют размер в зависимости от длины текста.  
  
-   Дает пользователям возможность легко копировать заголовок сообщения, текст, текст кнопок и ссылки на разделы справки (если таковые имеются) в буфер обмена или отправлять эти сведения в электронных сообщениях.  
  
-   Отобразить все базовые исключения и ошибки в дереве иерархических связей, когда пользователь щелкает **дополнительной информацией**.  
  
-   Дает пользователям возможность решать, нужно ли отображать сообщение при повторении одного и того же исключения.  
  
-   Обеспечивает доступ к справке в Интернете с помощью ссылки на раздел справки, связанный с тем или иным исключением.  
  
 Дополнительные сведения см. в разделе [окно сообщения об исключении программы](../../../2014/database-engine/dev-guide/program-exception-message-box.md).  
  
  