# Day 23 - 10 March 2025

1) Downloading Visual Studio Code from [official website](https://code.visualstudio.com/)
2) Understanding all the way to how to use [visual studio](https://www.youtube.com/watch?v=B-s71n0dHUk)
3) Practiced basic tasks like creating a new file, saving it, and running a simple Python script using the terminal inside VS Code.
4) Understanding the functions from visual studio code [web site](https://code.visualstudio.com/docs)
5) Downloading [UV](https://docs.astral.sh/uv/getting-started/installation/#standalone-installer) for more fast outputs
6) Understanding how does uv work from [website](https://github.com/astral-sh/uv)
7) Also went through some [YouTube videos](https://www.youtube.com/watch?v=igWlYl3asKw) to better understand the installation and usage of uv.
8) Learning the features from the [website](https://docs.astral.sh/uv/getting-started/features/)

#Installing UV 

***Running steps for installing***
```powershell
irm https://astral.sh/uv/install.ps1 | iex
```
```powershell
pip install uv
```

#Creating a project 
-Open your terminal

***Navigate to the folder***
```bash
cd D:\
```

***Initialize a new Python environment using uv***
```bash
uv venv
```

***Activate the environment***
```bash
.venv\Scripts\activate
```

***Create a pyproject.toml file***
```bash
uv init
```

***Opening the Visual Studio code with uv***
```bash
code .
```
