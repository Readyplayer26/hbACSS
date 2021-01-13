# Running and Benchmarking hbACSS

You need to docker to run the benchmarks, which follows [these instructions](docs/development/getting-started.rst#managing-your-development-environment-with-docker-compose).

The key steps are:

1. Install `Docker`_. (For Linux, see `Manage Docker as a non-root user`_) to
   run ``docker`` without ``sudo``.)

2. Install `docker-compose`.

If the above went all well, you should be setup for running the benchmarks.

## Running benchmarks and generating data points for hbACSS

You need to start a shell session in a container:
```
$ docker-compose run --rm honeybadgermpc bash
```

Then, to rerun the datapoints, you can use:
```
$ pytest --benchmark-save=hbavss_dummy_pcl --benchmark-min-rounds=3 --benchmark-warmup-iterations=0 benchmark/test_benchmark_hbavss_loglin.py
$ pytest --benchmark-save=pcl_detailed --benchmark-min-rounds=3 --benchmark-warmup-iterations=0 benchmark/test_benchmark_poly_commit_log.py
$ pytest --benchmark-save=hbavss_actual_pcl --benchmark-min-rounds=3 --benchmark-warmup-iterations=0 benchmark/test_benchmark_hbavss_actual_loglin.py
$ pytest --benchmark-save=hbacss2_dummy_pcl --benchmark-min-rounds=3 --benchmark-warmup-iterations=0 benchmark/test_benchmark_hbacss2_dummy_pcl.py
```

This would save the results under `.benmarks` in the same format as [DataWinterfell](../Datawinterfell).

## Running benchmarks and generating data points for AMT

TODO: Added later

## Generating graphs

We've already included the data in our previous runs of benchmarks under [DataWinterfell](../Datawinterfell)

You can then run the gengraphs:
```
$ python polycommit_loglin_gengraphs.py
```
This doesn't have to be running in container.