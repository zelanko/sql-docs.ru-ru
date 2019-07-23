---
title: Шаг 1. Настройка среды разработки pyodbc Python | Документация Майкрософт
ms.custom: ''
ms.date: 07/06/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 74e69704-e63c-450b-9207-5c1491d0e0f5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a1a43540d866faaf79b1c020eb255689862e6d97
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992521"
---
# <a name="step-1-configure-development-environment-for-pyodbc-python-development"></a>Шаг 1. Настройка среды разработки для использования pyodbc в Python

## <a name="windows"></a>Windows  
Подключение к базе данных SQL с помощью Python-pyodbc в Windows:
  
1. **Скачайте установщик Python**.  
  Если на компьютере отсутствует Python, установите его. Перейдите на [страницу загрузки Python](https://www.python.org/downloads/windows/) и скачайте соответствующий установщик. Например, если вы используете 64-разрядный компьютер, скачайте установщик Python 2,7 или 3,7 (x64).  
  
2. **Установите Python**.  После загрузки установщика выполните следующие действия: a. Дважды щелкните файл, чтобы запустить установщик. Б. Выберите язык и примите условия. в. Следуйте инструкциям на экране, и на компьютере должен быть установлен Python. г. Чтобы убедиться, что Python установлен, можно перейти на `C:\Python27` или `C:\Python37` и запустить `python -V` или `py -V` (для 3. x). 
      
3. [**Установка Microsoft ODBC Driver for SQL Server в Windows**](../../odbc/windows/system-requirements-installation-and-driver-files.md#installing-microsoft-odbc-driver-for-sql-server)
  
4. **Откройте cmd. exe от имени администратора**     

5. **Установка pyodbc с помощью PIP — диспетчер пакетов Python** (Замените `C:\Python27\Scripts` установленным путем Python)
```  
> cd C:\Python27\Scripts  
> pip install pyodbc  
```  

  
## <a name="linux"></a>Linux 
Подключение к базе данных SQL с помощью Python-pyodbc:
  
1. **Открыть терминал**  

2. [**Установка Microsoft ODBC Driver for SQL Server в Linux**](../../odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)

3.  **Установка pyodbc**  
```  
> sudo -H pip install pyodbc
```
