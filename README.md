# \# Multi-Stage SOC Investigation Lab

# 

# \## Project Overview

# 

# A home SOC lab built using Splunk Enterprise, Sysmon, Universal Forwarder, and Windows telemetry to simulate endpoint attacks, investigate incidents, and develop detection rules.

# 

# \## Current Progress

# 

# ✅ Milestone 1 - Lab Setup

# &#x20;   • Ubuntu Splunk Enterprise

# &#x20;   • Windows 11 Endpoint

# &#x20;   • Universal Forwarder

# &#x20;   • Data forwarding (9997)

# &#x20;   • Custom index (soc\_endpoint)

# 

# ✅ Milestone 2 - Endpoint Telemetry

# &#x20;   • Sysmon installed

# &#x20;   • SwiftOnSecurity Sysmon configuration

# &#x20;   • Splunk Add-on for Microsoft Windows

# &#x20;   • Windows Event Logs

# &#x20;   • Sysmon Event Logs

# 

# 🚧 Milestone 3

# &#x20;   Detection Engineering (In Progress)

# 

# \## Architecture

# 

# Windows Endpoint

# &#x20;     │

# &#x20;     │ Universal Forwarder

# &#x20;     ▼

# Splunk Enterprise (Ubuntu)

# &#x20;     │

# &#x20;     ▼

# soc\_endpoint Index

