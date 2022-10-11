---
title: "Python Environment"
date: 2021-12-12T23:22:14-06:00
draft: false
category: Environments
tags:
- Development
- Python
---

## Create and start Python Virtual Environment
{{< highlight bash >}}
python3 -m venv venv
source venv/bin/activate
{{< / highlight >}}

## To install a local requirements.txt
{{< highlight bash >}}
venv/bin/pip install -r requirements.txt
venv/bin/pip install gunicorn
{{< / highlight >}}

## To Exit Venv
{{< highlight bash >}}
deactivate
{{< / highlight >}}

## To create requirements.txt
{{< highlight bash >}}
pip freeze > requirements.txt
{{< / highlight >}}

## To remove installed plugins
{{< highlight bash >}}
pip freeze | xargs pip uninstall -y
{{< / highlight >}}

## To run flask app
{{< highlight bash >}}
flask app.py
{{< / highlight >}}
