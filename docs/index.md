# Perf Report!

Perf Report is a free program to generate a full systems performance PDF report on a kubernetes cluster.

Below is a list of general performance engineering resources (and some kubernetes resources too).


## Performance Resources

  * 60 second analysis from Section 3.3 of [BPF Performance Tools](https://www.brendangregg.com/bpf-performance-tools-book.html)
  * [Chapter resources from the BPF Performance Tools book](https://github.com/brendangregg/bpf-perf-tools-book/tree/master/originals)
  * [bpftrace man page](https://manpages.ubuntu.com/manpages/focal/en/man8/bpftrace.bt.8.html)
  * [Linux Tracing Docs - kernel version 5.4](https://www.kernel.org/doc/html/v5.4/trace/index.html)
  * [Linux Tracing BPF Docs - kernel version 5.4](https://www.kernel.org/doc/html/v5.4/bpf/index.html)
  * [Linux Tracing Technologies](https://docs.kernel.org/trace/index.html)
  * [Cilium BPF and XDP Reference Guide](https://docs.cilium.io/en/latest/bpf/)
  * [Cilium BPF and XDP Reference Guide - Further Reading](https://docs.cilium.io/en/latest/bpf/resources/#further-reading)
  * [https://www.brendangregg.com/perf.html](https://www.brendangregg.com/perf.html)
  * [https://github.com/brendangregg/FlameGraph](https://github.com/brendangregg/FlameGraph)
  * [https://github.com/Netflix/flamescope](https://github.com/Netflix/flamescope)
  * [https://github.com/iovisor/kubectl-trace](https://github.com/iovisor/kubectl-trace)
  * [https://man7.org/index.html](https://man7.org/index.html)
  * [https://github.com/kvaps/kubectl-node-shell](https://github.com/kvaps/kubectl-node-shell)
  * [https://www.kernel.org/doc/Documentation/trace/events.txt](https://www.kernel.org/doc/Documentation/trace/events.txt)
  * [https://www.kernel.org/doc/Documentation/trace/tracepoints.txt](https://www.kernel.org/doc/Documentation/trace/tracepoints.txt)
  * [https://perf.wiki.kernel.org/index.php/Main_Page](https://perf.wiki.kernel.org/index.php/Main_Page)
  * [https://github.com/iovisor/bpftrace](https://github.com/iovisor/bpftrace)
  * [https://github.com/iovisor/bpftrace#tools](https://github.com/iovisor/bpftrace#tools)
  * [https://github.com/iovisor/bpftrace/tree/master/tools](https://github.com/iovisor/bpftrace/tree/master/tools)
  * [https://github.com/iovisor/bcc](https://github.com/iovisor/bcc)
  * [https://github.com/iovisor/bcc/tree/master/examples](https://github.com/iovisor/bcc/tree/master/examples)
  * [https://github.com/iovisor/ply](https://github.com/iovisor/ply)
  * [PXL Scripts Overview](https://github.com/pixie-io/pixie/tree/main/src/pxl_scripts)
  * [https://www.brendangregg.com/ebpf.html](https://www.brendangregg.com/ebpf.html)
  * [https://www.brendangregg.com/blog/2019-01-01/learn-ebpf-tracing.html](https://www.brendangregg.com/blog/2019-01-01/learn-ebpf-tracing.html)
  * [https://github.com/iovisor/bpftrace/blob/master/docs/reference_guide.md](https://github.com/iovisor/bpftrace/blob/master/docs/reference_guide.md)
  * [bpftrace probes](https://github.com/iovisor/bpftrace/blob/master/docs/reference_guide.md#probes)
  * [bpftrace variables](https://github.com/iovisor/bpftrace/blob/master/docs/reference_guide.md#variables)
  * [https://github.com/brendangregg/pmc-cloud-tools](https://github.com/brendangregg/pmc-cloud-tools)
  * [Ilya Grigorik homepage](https://www.igvita.com/)
  * [C++ Core Guidelines - Performance](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#S-performance)


## Books and Videos

  * [https://www.brendangregg.com/systems-performance-2nd-edition-book.html](https://www.brendangregg.com/systems-performance-2nd-edition-book.html)
  * [https://www.brendangregg.com/bpf-performance-tools-book.html](https://www.brendangregg.com/bpf-performance-tools-book.html)
  * [https://www.amazon.com/Art-Writing-Efficient-Programs-optimizations/dp/1800208111](https://www.amazon.com/Art-Writing-Efficient-Programs-optimizations/dp/1800208111)
  * [Very important video: Mike Acton discussing data-oriented design](https://www.youtube.com/watch?v=rX0ItVEVjHc)
  * [Mike Acton at HandmadeCon 2015](https://www.youtube.com/watch?v=qWJpI2adCcs)
  * [Cloud Performance Root Cause Analysis at Netflix • Brendan Gregg • YOW! 2018](https://www.youtube.com/watch?v=LLZmTuTSEB8)
  * [Brendan Gregg talks about Extended BPF - A new software type](https://www.youtube.com/watch?v=7pmXdG8-7WU)
  * [CppCon 2017: Carl Cook "When a Microsecond Is an Eternity: High Performance Trading Systems in C++" - whole video is great, but pointed to a fun part of the video](https://www.youtube.com/watch?v=NH1Tta7purM&t=2271s)
  * [Ilya Grigorik - Mobile frontends and networking - Breaking the 1000ms Time to Glass Mobile Barrier](https://www.youtube.com/watch?v=Il4swGfTOSM)
  * [Ilya Grigorik - High Performance Browser Networking - O'Reilly ](https://www.igvita.com/)
  * [The Linux Programming Interface](https://man7.org/tlpi/index.html)
  * [CppCon 2017: Fedor Pikus "C++ atomics, from basic to advanced. What do they really do?"](https://www.youtube.com/watch?v=ZQFzMfHIxng)
  * [Branchless Programming in C++ - Fedor Pikus - CppCon 2021](https://www.youtube.com/watch?v=g-WPhYREFjk)
  * [CppCon 2016: Fedor Pikus "The speed of concurrency (is lock-free faster?)"](https://www.youtube.com/watch?v=9hJkWwHDDxs)
  * [Core C++ 2019 :: Avi Kivity :: Building efficient I/O intensive applications with Seastar](https://www.youtube.com/watch?v=p8d28t4qCTY)
  * [How to Make Linux Microservice-Aware with Cilium and eBPF](https://www.youtube.com/watch?v=_Iq1xxNZOAo)
  * [Designing Data-Intensive Applications](https://www.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/)
  * [Production Kubernetes](https://www.oreilly.com/library/view/production-kubernetes/9781492092292/)
  * [Building Event-Driven Microservices](https://www.oreilly.com/library/view/building-event-driven-microservices/9781492057888)
  * [A Guided Tour of Cilium Service Mesh - Liz Rice, Isovalent](https://www.youtube.com/watch?v=e10kDBEsZw4)
  * [Hello eBPF! Goodbye Sidecar?](https://www.youtube.com/watch?v=ThtRT8dhu8c)


## Observability Tools

  * [https://www.instana.com/](https://www.instana.com/)
  * [https://sysdig.com/](https://sysdig.com/)
  * [https://www.loggly.com/](https://www.loggly.com/)
  * [https://grafana.com/](https://grafana.com/)
  * [Atlas time series datastore](https://netflix.github.io/atlas-docs/)
  * [Istio Observability](https://istio.io/latest/docs/concepts/observability/)
  * [Pixie](https://px.dev/)
  * [Cilium and Hubble](https://github.com/cilium/hubble)


## Documentation and Dataviz Resources

  * [https://pandoc.org/](https://pandoc.org/)
  * [https://godotengine.org/](https://godotengine.org/)
  * [https://galaxy.opensyllabus.org/](https://galaxy.opensyllabus.org/)


## Courses

  * [Ilya Grigorik - Website Performance Optimization - The Critical Rendering Path](https://www.udacity.com/course/website-performance-optimization--ud884)
  * [MIT OCW - Performance Engineering Of Software Systems](https://ocw.mit.edu/courses/6-172-performance-engineering-of-software-systems-fall-2018/video_galleries/lecture-videos/)
  * [Kube Academy](https://kube.academy/)


## Analysis by Component

 * [Install](analysis/Install.md)
 * [CPU](analysis/CPU.md)
 * [Memory](analysis/Memory.md)
 * [Filesystem or Disk](analysis/FilesystemDisk.md)
 * [Network](analysis/Network.md)