---
title: Предоставление прав гостя для компьютера веб-сервера | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bddf6ce0bbfb78435118ef3d87303a94c792c96d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922649"
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Предоставление прав гостя для компьютера веб-сервера
Учетная запись анонимного веб-сервера (IUSR_*ComputerName*) должна быть добавлена в локальную группу гостей на компьютере веб-сервера для использования RDS.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Предоставление прав гостя для компьютера веб-сервера  
  
1.  На компьютере сервера Microsoft Windows 2000 нажмите кнопку **Пуск**, укажите пункт **программы**, затем **Администрирование**и выберите пункт **Управление компьютером**.  
  
2.  В дереве консоли в области **Локальные пользователи и группы**щелкните **группы**.  
  
3.  Выберите локальную группу **гостей** . В меню **действие** выберите пункт **свойства**.  
  
4.  В диалоговом окне **Свойства: гости** нажмите кнопку **Добавить**.  
  
5.  Если анонимная учетная запись веб-сервера не отображается в списке в диалоговом окне **Выбор пользователей или групп** , введите имя (IUSR_*ComputerName*) в нижнем пустом поле и нажмите кнопку **добавить**.  
  
6.  Нажмите кнопку **ОК**.


