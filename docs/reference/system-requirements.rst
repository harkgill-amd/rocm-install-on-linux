.. meta::
  :description: System requirements for AMD ROCm
  :keywords: Linux support, ROCm distributions, system requirements, supported GPUs,  Instinct,
    Radeon PRO, Radeon, AMD, ROCm

.. _system-requirements:

**************************************************************************************
System requirements (Linux)
**************************************************************************************

.. |br| raw:: html

   <br>

Supported GPUs
=============================================

The following table shows the supported AMD Instinct™ accelerators, and Radeon™ PRO
and Radeon GPUs. If a GPU is not listed on this table, it's not officially supported by AMD.

Accelerators and GPUs listed in the following table support compute workloads (no display information or graphics). If you’re using ROCm with AMD Radeon or Radeon Pro GPUs for graphics workloads, see the `Use ROCm on Radeon GPU documentation <https://rocm.docs.amd.com/projects/radeon/en/latest/docs/compatibility.html>`_ to verify compatibility and system requirements.

.. tab-set::

  .. tab-item:: AMD Instinct

    .. csv-table::
      :widths: 50, 25, 25, 10
      :header: "Accelerator", "Architecture", "LLVM target", "Support"

      "AMD Instinct MI325X", "CDNA3", "gfx942", "✅ [#ub2204]_"
      "AMD Instinct MI300X", "CDNA3", "gfx942", "✅"
      "AMD Instinct MI300A", "CDNA3", "gfx942", "✅"
      "AMD Instinct MI250X", "CDNA2", "gfx90a", "✅"
      "AMD Instinct MI250", "CDNA2", "gfx90a", "✅"
      "AMD Instinct MI210", "CDNA2", "gfx90a", "✅"
      "AMD Instinct MI100", "CDNA", "gfx908", "✅"
      "AMD Instinct MI50", "GCN5.1", "gfx906", "⚠️"
      "AMD Instinct MI25", "GCN5.0", "gfx900", "❌"

  .. tab-item:: AMD Radeon PRO

    .. csv-table::
      :widths: 50, 25, 25, 10
      :header: "GPU", "Architecture", "LLVM target", "Support"

      "AMD Radeon PRO V710", "RDNA3", "gfx1101", "✅"
      "AMD Radeon PRO W7900 Dual Slot", "RDNA3", "gfx1100", "✅"
      "AMD Radeon PRO W7900", "RDNA3", "gfx1100", "✅"
      "AMD Radeon PRO W7800", "RDNA3", "gfx1100", "✅"
      "AMD Radeon PRO W6800", "RDNA2", "gfx1030", "✅"
      "AMD Radeon PRO V620", "RDNA2", "gfx1030", "✅"
      "AMD Radeon PRO VII", "GCN5.1", "gfx906", "⚠️"

  .. tab-item:: AMD Radeon

    .. csv-table::
      :widths: 50, 25, 25, 10
      :header: "GPU", "Architecture", "LLVM target", "Support"

      "AMD Radeon RX 7900 XTX", "RDNA3", "gfx1100", "✅"
      "AMD Radeon RX 7900 XT", "RDNA3", "gfx1100", "✅"
      "AMD Radeon RX 7900 GRE", "RDNA3", "gfx1100", "✅"
      "AMD Radeon VII", "GCN5.1", "gfx906", "⚠️"

✅: **Supported** - Official software distributions of the current ROCm release fully support this hardware.

⚠️: **Deprecated** - The current ROCm release has limited support for this hardware. Existing features and capabilities are maintained, but no new features or optimizations will be added. A future ROCm release will remove support.

❌: **Unsupported** - The current ROCm release does not support this hardware. The HIP runtime might continue to run applications for an unsupported GPU, but prebuilt ROCm libraries are not officially supported and will cause runtime errors.

.. important:: 

   Systems with multiple GPUs may require ``iommu=pt`` to be set at boot time to prevent application hangs, as described in
   :ref:`multi-gpu`.

.. note::

   See the :ref:`Compatibility matrix <rocm:architecture-support-compatibility-matrix>` for an overview
   of supported GPU architectures across ROCm releases.

.. _supported_distributions:

Supported operating systems
=============================================

AMD ROCm software supports the following Linux distributions.

.. csv-table::
    :widths: 50, 50, 25
    :header: "Operating system", "Kernel", "Support"
    :escape: \

    "Ubuntu 24.04.2", "6.8 [GA], 6.11 [HWE]", "✅"
    "Ubuntu 22.04.5", "5.15 [GA], 6.8 [HWE]", "✅"
    "RHEL 9.5", "5.14.0", "✅"
    "RHEL 9.4", "5.14.0", "✅"
    "RHEL 8.10", "4.18.0", "✅"
    "SLES 15 SP6", "6.4.0", "✅"
    "SLES 15 SP5", "5.14.21", "✅"
    "Oracle Linux 8.10", "5.15.0", "✅ [#mi300x]_"
    "Debian 12", "6.1", "✅ [#mi300x]_"

.. note::

   See the :doc:`rocm:compatibility/compatibility-matrix` for an overview
   of OS support across ROCm releases.

Virtualization support
=============================================

ROCm supports virtualization for select GPUs only as shown below.

.. csv-table::
    :widths: 20, 20, 20, 40
    :header: "Hypervisor", "Version", "GPU", "Validated guest OS (kernel)"

    "VMWare", "ESXi 8.0.3", "MI210", "Ubuntu 22.04.5 (6.8 [HWE]), |br| SLES 15 SP5 (5.14.21), |br| RHEL 9.4 (5.14.0)"
    "VMWare", "ESXi 7.0.3", "MI210", "Ubuntu 22.04.5 (6.8 [HWE]), |br| RHEL 9.4 (5.14.0)"

CPU support
=============================================

ROCm requires CPUs that support PCIe™ atomics. Modern CPUs after the release of
1st generation AMD Zen CPU and Intel™ Haswell support PCIe atomics.

.. rubric:: Footnotes

.. [#ub2204] AMD Instinct MI325X is supported only on Ubuntu 22.04.5 [5.15 GA].
.. [#mi300x] Oracle Linux 8.10 and Debian 12 are supported only on AMD Instinct MI300X.
