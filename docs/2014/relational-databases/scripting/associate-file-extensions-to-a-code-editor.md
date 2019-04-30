---
title: Связывание расширения файла с редактором кода | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- file extensions [SQL Server]
- associating file extensions [SQL Server]
- Query Editor [SQL Server Management Studio], associating file extensions
ms.assetid: 193630f4-93de-4950-8f36-68702531f925
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed0338f921b3d143c5b7a42bc73ae22db4148c7c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63209531"
---
# <a name="associate-file-extensions-to-a-code-editor"></a>Связывание расширения файла с редактором кода
  Связь расширений файлов с конкретным редактором кода позволяет открывать файл соответствующим редактором кода среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] двойным щелчком файла в проводнике Windows. Расширения, обычно используемые средой [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], такие как SQL и MDX, задаются во время установки. Новые расширения файлов должны быть связаны со средой [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] в файловой системе. Эту возможность можно использовать для открытия файлов, созданных в других редакторах, или для открытия переименованных файлов, таких как резервные копии SQL-файлов, переименованных в файлы с расширением BAK.  
  
 Этот процесс включает два шага. Вначале нужно связать расширение со средой [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем — с конкретным редактором кода.  
  
### <a name="to-associate-a-new-file-extension-with-sql-server-management-studio"></a>Связывание нового расширения файла со средой SQL Server Management Studio  
  
1.  В меню **Пуск** последовательно укажите **Все программы**, **Стандартные**, **Проводник**.  
  
2.  В проводнике Windows в меню **Сервис** выберите **Свойства папки**.  
  
3.  В диалоговом окне **Свойства папки** на вкладке **Типы файлов** нажмите кнопку **Создать**.  
  
4.  В диалоговом окне **Создание нового расширения** в поле **Расширение** введите новое расширение файла, которое нужно задать, и нажмите кнопку **ОК**. Не ставьте перед расширением точку.  
  
5.  В списке **Зарегистрированные типы файлов** выберите новое расширение и нажмите **Изменить**.  
  
6.  В диалоговом окне **Открыть с помощью** выберите пункт **SSMS — среда SQL Server Management Studio** и нажмите кнопку **ОК**.  
  
7.  Нажмите **Закрыть** , чтобы закрыть диалоговое окно **Свойства папки** , и закройте проводник Windows.  
  
### <a name="to-associate-a-new-file-extension-with-a-code-editor-in-sql-server-management-studio"></a>Связывание нового расширения файла с редактором кода в среде SQL Server Management Studio  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]в меню **Сервис** выберите **Параметры**.  
  
2.  В диалоговом окне **Параметры** щелкните **Текстовый редактор**, а затем — **Расширение файла**.  
  
3.  В поле **Расширение** введите новое расширение файла.  
  
4.  В поле **Редактор** выберите редактор кода, который хотите использовать для открытия данного типа файлов, нажмите кнопку **Добавить**, а затем кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Программа SSMS](../../ssms/ssms-utility.md)  
  
  
