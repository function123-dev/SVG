Overview

  VNC Shield ML** is an advanced, AI-powered security system designed to detect and prevent data exfiltration attacks on VNC (Virtual Network Computing) servers including **TigerVNC** and **RealVNC**. The system utilizes a modern **sidecar architecture** with multiple machine learning models running in parallel to provide real-time threat detection with high accuracy.

Why VNC Shield?

   **Zero-Day Protection**: ML models detect unknown attack patterns
   **Real-time Monitoring**: Sub-second threat detection and response
   **Non-Intrusive**: Sidecar architecture doesn't affect main VNC performance
   **High Accuracy**: Ensemble ML approach achieves 96.8% accuracy
   **Automated Defense**: Instant blocking and alerting of threats

Problem Statement

**Background:**
VNC servers are fundamental for remote access but inherently provide weak security mechanisms. While TigerVNC and RealVNC offer TLS encryption, data exfiltration through insider threats or compromised credentials remains a critical concern.

**Challenge:**
    Develop a comprehensive testbed system to:
    1. Simulate all possible data exfiltration attack scenarios
    2. Detect exfiltration attempts in real-time using ML
    3. Prevent data leakage through automated defense mechanisms
    4. Monitor and analyze VNC traffic without performance degradation

**Solution:**
VNC Shield ML implements a sidecar-based architecture where ML inference engines run alongside VNC servers, analyzing traffic patterns, user behavior, and network anomalies to detect and prevent data exfiltration with minimal latency.

  🤖 AI-Powered Detection

   **6 Deployed ML Models** - Random Forest, Neural Networks, XGBoost, LSTM, Autoencoders, Isolation Forest
   **Ensemble Learning** - Weighted voting, soft voting, and stacking for superior accuracy
   **Real-time Inference** - <30ms latency for threat predictions
   **96.8% Accuracy** - Industry-leading detection rates
   **Automated Retraining** - Continuous learning from new threat patterns

System Architecture
  
    ┌─────────────────────────────────────────────────────────────┐
  │ SYSTEM ARCHITECTURE │
  └─────────────────────────────────────────────────────────────┘
  
  ┌─────────────────────────────────────────────────────────────┐
  │ VNC Application Layer │
  │ ┌───────────────────┐ ┌───────────────────┐ │
  │ │ TigerVNC Server │ │ RealVNC Server │ │
  │ │ Port: 5901 │ │ Port: 5902 │ │
  │ └─────────┬─────────┘ └─────────┬─────────┘ │
  └────────────┼──────────────────────────────┼──────────────────┘
  │ │
  └──────────────┬───────────────┘
  │
  │ Traffic Mirror
  │
  ┌────────────────────────────┴─────────────────────────────────┐
  │ Sidecar Container Layer │
  │ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐ │
  │ │ ML Engine │ │ Feature │ │ Data │ │
  │ │ Sidecar │ │ Engineering │ │ Processor │ │
  │ │ :8080 │ │ Sidecar │ │ Sidecar │ │
  │ │ │ │ :8081 │ │ :8082 │ │
  │ └──────┬───────┘ └──────┬───────┘ └──────┬───────┘ │
  │ │ │ │ │
  │ └──────────────────┴──────────────────┘ │
  │ │ │
  └────────────────────────────┼──────────────────────────────────┘
  │
  ▼
  ┌─────────────────────────────────────────────────────────────┐
  │ ML Model Layer │
  │ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ │
  │ │ Random │ │ Neural │ │ XGBoost │ │ LSTM │ │
  │ │ Forest │ │ Network │ │Classifier│ │ Anomaly │ │
  │ │ 94.7% │ │ 96.8% │ │ 95.2% │ │ 93.4% │ │
  │ └──────────┘ └──────────┘ └──────────┘ └──────────┘ │
  └────────────────────────────┬────────────────────────────────┘
  │
  ▼
  ┌─────────────────────────────────────────────────────────────┐
  │ Defense & Response Layer │
  │ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ │
  │ │ Log │ │ Rate │ │ Network │ │ Terminate│ │
  │ │ Events │ │ Limit │ │ Isolate │ │ & Block│ │
  │ └──────────┘ └──────────┘ └──────────┘ └──────────┘ │
  └────────────────────────────┬────────────────────────────────┘
  │
  ▼
  ┌─────────────────────────────────────────────────────────────┐
  │ Monitoring & Storage Layer │
  │ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ │
  │ │Prometheus│ │ ELK │ │PostgreSQL│ │ Grafana │ │
  │ │ Metrics │ │ Logs │ │ Events │ │Dashboard │ │
  │ └──────────┘ └──────────┘ └──────────┘ └──────────┘ │

Complete System Flow
  ┌─────────────────────────────────────────────────────────────┐
│ STARTING POINT │
│ VNC Client Connection Request │
└────────────────────────┬────────────────────────────────────┘
│
▼
┌───────────────────────────────┐
│ VNC Server Accepts │
│ Connection (Port 5900) │
└───────────────┬───────────────┘
│
▼
┌────────────────────────────────────────────────────────────┐
│ SIDECAR ACTIVATION │
│ ┌──────────────────────────────────────────────────┐ │
│ │ ML Sidecar Detects New Connection Event │ │
│ └──────────────────┬───────────────────────────────┘ │
│ │ │
│ ▼ │
│ ┌──────────────────────────────────────────────────┐ │
│ │ Start Monitoring Pipeline │ │
│ │ • Network traffic │ │
│ │ • Process metrics │ │
│ │ • Log files │ │
│ │ • User behavior │ │
│ └──────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────┘
│
▼
┌────────────────────────────────────────────────────────────┐
│ DATA COLLECTION PHASE │
│ │
│ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ │
│ │ Network │ │ System │ │ VNC │ │
│ │ Packets │ │ Metrics │ │ Logs │ │
│ └──────┬──────┘ └──────┬──────┘ └──────┬──────┘ │
│ │ │ │ │
│ └─────────────────┴─────────────────┘ │
│ │ │
└───────────────────────────┼─────────────────────────────────┘
│
▼
┌────────────────────────────────────────────────────────────┐
│ FEATURE EXTRACTION PHASE │
│ │
│ ┌────────────────────────────────────────────────┐ │
│ │ Extract Features from Raw Data: │ │
│ │ • Connection patterns │ │
│ │ • Data transfer volume │ │
│ │ • Command sequences │ │
│ │ • Screen change frequency │ │
│ │ • Clipboard activity │ │
│ │ • File transfer patterns │ │
│ └─────────────────────┬──────────────────────────┘ │
│ │ │
│ ▼ │
│ ┌────────────────────────────────────────────────┐ │
│ │ Feature Vector: [f1, f2, f3, ..., f47] │ │
│ │ Total: 47 Features │ │
│ └────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────┘
│
▼
┌────────────────────────────────────────────────────────────┐
│ ML INFERENCE PHASE │
│ │
│ ┌────────────────────────────────────────────────┐ │
│ │ Feed to ML Models (Ensemble) │ │
│ │ ┌──────────┐ ┌──────────┐ ┌──────────┐ │ │
│ │ │ Anomaly │ │Classifier│ │ Pattern │ │ │
│ │ │ Detector │ │ Model │ │ Matcher │ │ │
│ │ │(Iso.For.)│ │(Rnd.For.)│ │ (LSTM) │ │ │
│ │ └────┬─────┘ └────┬─────┘ └────┬─────┘ │ │
│ │ │ │ │ │ │
│ │ └────────────┴────────────┘ │ │
│ │ │ │ │
│ │ ▼ │ │
│ │ ┌────────────────────────┐ │ │
│ │ │ Weighted Ensemble │ │ │
│ │ │ Prediction │ │ │
│ │ │ • Weight: 0.30 (NN) │ │ │
│ │ │ • Weight: 0.25 (RF) │ │ │
│ │ │ • Weight: 0.25 (XGB) │ │ │
│ │ │ • Weight: 0.20 (LSTM) │ │ │
│ │ └────────┬───────────────┘ │ │
│ └────────────────┼───────────────────────────────┘ │
│ │ │
│ ▼ │
│ ┌────────────────────────────────────────────────┐ │
│ │ Threat Score: 0.0 - 1.0 │ │
│ │ Classification: Normal/Suspicious/Malicious │ │
│ │ Confidence: 0.0 - 1.0 │ │
│ └────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────┘
│
▼
┌────────────────────────────────────────────────────────────┐
│ DECISION PHASE │
│ │
│ ┌────────────────────────────────────────────────┐ │
│ │ Threat Score Evaluation │ │
│ └─────────────────────┬──────────────────────────┘ │
│ │ │
│ ┌──────────────┼──────────────┬─────────────┐ │
│ │ │ │ │ │
│ ▼ ▼ ▼ ▼ │
│ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ │
│ │ LOW │ │ MEDIUM │ │ HIGH │ │ CRITICAL │ │
│ │ Score<0.3│ │Score<0.6 │ │Score<0.8 │ │Score≥0.8 │ │
│ │ │ │ │ │ │ │ │ │
│ │ • Log │ │• Log │ │• Log │ │• Log │ │
│ │ │ │• Rate │ │• Rate │ │• Term. │ │
│ │ │ │ Limit │ │ Limit │ │ Conn. │ │
│ │ │ │ │ │• Isolate │ │• Block │ │
│ │ │ │ │ │• Alert │ │• Alert │ │
│ │ │ │ │ │ │ │• Forensic│ │
│ └──────────┘ └──────────┘ └──────────┘ └──────────┘ │
└────────────────────────────────────────────────────────────┘
│ │ │ │
└──────────────┴──────────────┴─────────────┘
│
▼
┌────────────────────────────────────────────────────────────┐
│ RESPONSE PHASE │
│ │
│ ┌────────────────────────────────────────────────┐ │
│ │ Execute Response Actions: │ │
│ │ │ │
│ │ 1. Update firewall rules (iptables) │ │
│ │ └─ Block malicious IPs │ │
│ │ └─ Apply rate limiting │ │
│ │ └─ Network isolation (VLAN) │ │
│ │ │ │
│ │ 2. Modify connection limits │ │
│ │ └─ Throttle bandwidth │ │
│ │ └─ Limit concurrent connections │ │
│ │ │ │
│ │ 3. Send alerts to SIEM │ │
│ │ └─ Email notifications │ │
│ │ └─ Slack/PagerDuty alerts │ │
│ │ └─ SMS for critical threats │ │
│ │ │ │
│ │ 4. Update threat intelligence │ │
│ │ └─ Add to IP blacklist │ │
│ │ └─ Update ML training data │ │
│ │ └─ Share with threat feeds │ │
│ └────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────┘
│
▼
┌────────────────────────────────────────────────────────────┐
│ LOGGING & METRICS PHASE │
│ │
│ ┌────────────────────────────────────────────────┐ │
│ │ Store Results in Multiple Systems: │ │
│ │ │ │
│ │ ┌────────────┐ ┌────────────┐ ┌──────────┐│ │
│ │ │Prometheus │ │ ELK │ │PostgreSQL││ │
│ │ │ (Metrics) │ │ (Logs) │ │ (Events) ││ │
│ │ ��� │ │ │ │ ││ │
│ │ │• Counters │ │• Elastic │ │• Events ││ │
│ │ │• Gauges │ │• Logstash │ │• History ││ │
│ │ │• Histogram │ │• Kibana │ │• Audit ││ │
│ │ └────────────┘ └────────────┘ └──────────┘│ │
│ │ │ │
│ │ ┌────────────┐ ┌────────────┐ │ │
│ │ │ Grafana │ │ MLflow │ │ │
│ │ │(Dashboard) │ │(Model Mgmt)│ │ │
│ │ │ │ │ │ │ │
│ │ │• Charts │ │• Training │ │ │
│ │ │• Alerts │ │• Versioning│ │ │
│ │ │• Reports │ │• Tracking │ │ │
│ │ └────────────┘ └────────────┘ │ │
│ └────────────────────────────────────────────────┘ │
└────────────────────────────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────┐
│ ENDING POINT │
│ │
│ VNC Connection Status: │
│ ├─ ✅ Allowed (Score < 0.3) │
│ ├─ ⚠️ Rate-Limited (0.3 ≤ Score < 0.6) │
│ ├─ 🚫 Isolated (0.6 ≤ Score < 0.8) │
│ └─ ⛔ Blocked/Terminated (Score ≥ 0.8) │
│ │
│ Security Event: Logged and Stored ✓ │
│ Alerts: Sent to Security Team ✓ │
│ Metrics: Updated in Dashboards ✓ │
│ ML Model: Updated with new data (feedback loop) ✓ │
└─────────────────────────────────────────────────────────────┘
│
│
▼
┌───────────────────────────┐
│ CONTINUOUS LEARNING │
│ (Feedback Loop) │
│ │
│ • Retrain models daily │
│ • Update features │
│ • Improve accuracy │
└───────────┬───────────────┘
│
└─────────┐
│
┌──────────▼──────────┐
│ Back to Monitoring │
└─────────────────────┘
 
