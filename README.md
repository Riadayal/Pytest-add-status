# How to add test status in automation test in Pytest on [LambdaTest](https://www.lambdatest.com/?utm_source=github&utm_medium=repo&utm_campaign=Pytest-add-status)

If you want to add test status in automation test in Pytest on LambdaTest, you can follow the below steps. You can refer to sample test repo [here](https://github.com/LambdaTest/pytest-selenium-sample).

## Configure `conftest.py`

The driver function in `conftest.py` has to add "lambda-status" as "passed" or "failed" based on the execution. Add the below code to your driver function (refer to `conftest.py`):


```python
    def fin():
        #browser.execute_script("lambda-status=".format(str(not request.node.rep_call.failed if "passed" else "failed").lower()))
        if request.node.rep_call.failed:
            browser.execute_script("lambda-status=failed")
        else:
            browser.execute_script("lambda-status=passed")
            browser.quit()
    request.addfinalizer(fin)
```

## Run your test

```bash
cd tests //navigate to tests directory
python sample_todo.py
```

# Links:

[LambdaTest Community](http://community.lambdatest.com/)

