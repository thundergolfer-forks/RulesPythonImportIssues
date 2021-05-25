## Reproduction

Current 


```
======================================================================
ERROR: test_launch_template (__main__.DataflowMonitorTest)
DataflowMonitorTest.test_launch_template
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/lib/python3.8/unittest/mock.py", line 1325, in patched
    return func(*newargs, **newkeywargs)
  File "/home/codespace/.cache/bazel/_bazel_codespace/6169a4afe7d0cbdbab7fe9ff25ca97fd/sandbox/linux-sandbox/2/execroot/RulesPythonImportIssues/bazel-out/k8-fastbuild/bin/dataflow_test.runfiles/RulesPythonImportIssues/dataflow_test.py", line 31, in test_launch_template
    project_id = gcp_responses.PROJECT_ID
NameError: name 'gcp_responses' is not defined
```
