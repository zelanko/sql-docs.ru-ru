---
title: 'Шаг 1: Настройка среды разработки Python pyodbc | Документация Майкрософт'
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
caps.latest.revision: 2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f588174ea80677066628cb3e756d7c38bd42fba
ms.sourcegitcommit: 9cd01df88a8ceff9f514c112342950e03892b12c
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2018
ms.locfileid: "42787499"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Шаг 1. Настройка среды разработки для использования pyodbc в Python

## <a name="windows"></a>Windows  
Подключитесь к базе данных SQL с помощью Python — pyodbc на Windows:
  
1. **Скачайте установщик Python**.  
  Если компьютер не имеет Python, установите его. Перейдите к [странице загружаемых файлов Python](https://www.python.org/downloads/windows/) и загрузить соответствующий установщик. Например если вы используете 64-разрядном компьютере, скачайте установщик Python 2.7 или 3.7 (x 64).  
  
2. **Установите Python**.  После загрузки установщика, выполните следующие действия:. Дважды щелкните файл, чтобы запустить установщик. Б. Выберите язык и примите условия. в. Следуйте инструкциям на экране и Python должен быть установлен на компьютере. г. Убедитесь, что Python установлен, перейдя к `C:\Python27` или `C:\Python37` и запустите `python -V` или `py -V` (для 3.x) 
      
3. [**Установка Microsoft ODBC Driver for SQL Server в Windows**](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)
  
4. **Откройте cmd.exe с правами администратора**     

5. **Установите pyodbc с помощью pip - диспетчер пакетов Python** (Замените `C:\Python27\Scripts` с ваш путь установки Python)
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Подключитесь к базе данных SQL с помощью Python — pyodbc:
  
1. **Открыть терминал**  

2. [**Установка Microsoft ODBC Driver for SQL Server в Linux**](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

3.  **Установите pyodbc**  
```  
> sudo -H pip install pyodbc
```
