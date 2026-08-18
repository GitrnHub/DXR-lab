# DXR Lab

A small cloud-build lab for Microsoft's current DirectX Raytracing (DXR) samples.

This repository does **not** vendor the large `DirectX-Graphics-Samples` source tree. GitHub Actions downloads the current Microsoft source on demand, builds the DXR samples on a Windows runner, and publishes the compiled x64 Release output as a workflow artifact.

## What it builds

Tutorial samples:

- D3D12RaytracingHelloWorld
- D3D12RaytracingSimpleLighting
- D3D12RaytracingProceduralGeometry
- D3D12RaytracingLibrarySubobjects
- D3D12RaytracingHelloShaderExecutionReordering
- D3D12RaytracingSakuraForestSER
- D3D12RaytracingOpacityMicromaps

It also attempts the complete `D3D12Raytracing.slnx` build so advanced samples can be collected when their dependencies/toolchain are available.

## Build

Open **Actions → Build Microsoft DXR Samples → Run workflow**.

The workflow runs on `windows-2022`, restores NuGet dependencies, builds Release x64, then uploads:

`D3D12Raytracing-All-Samples-Release-x64`

Download the artifact ZIP and keep each sample's generated DLLs/resources beside its EXE.

## Hardware

Compilation happens in GitHub Actions. Actual DXR execution should be tested locally on a Windows machine with a DXR-capable GPU and current driver; standard hosted runners are not an RTX/DXR test machine.

## Upstream

Source is fetched at build time from `microsoft/DirectX-Graphics-Samples`.
