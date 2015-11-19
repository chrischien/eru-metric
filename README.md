Eru-Metric
==========

A library for watching container metrics and send to remote.

This repo implement open-falcon methods you can write your methods by your self.

How
===

1. write a func to implement Send method if you want send metircs to other place.

```
func Send(data map[string]float64, endpoint, tag string, timestamp, step int64) error
```

2. set metric global setting

```
SetGlobalSetting(client Remote, timeout, forceTimeout time.Duration, vlanPrefix, defaultVlan string)
```

3. create a backend object which implemented Send interface.

4. create a metric for each container.

```
CreateMetric(step time.Duration, client Remote, tag, endpoint string)
```

5. init metric object

```
InitMetric(cid string, pid int)
```

6. update, calcuate, save and send

```
UpdateStats(cid string)
CalcRate(info map[string]uint64, now time.Time)
SaveLast(info map[string]uint64)
Send(rate map[string]float64)
```

7. exit metirc

```
Exit()
```

Example
=======

see example.go only work under LINUX environment.

```
eru-metric CONTAINERID CONTAINERID ... CONTAINERID [-DEBUG] [-d docker remote addr] [-t transfer remote addr]
```

