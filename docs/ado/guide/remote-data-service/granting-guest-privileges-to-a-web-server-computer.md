---
description: Предоставление прав гостя для компьютера веб-сервера
title: Предоставление прав гостя для компьютера веб-сервера | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
author: rothja
ms.author: jroth
ms.openlocfilehash: d34e53f62b66197c7aaedcc0df57e489763c1dd0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978095"
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


