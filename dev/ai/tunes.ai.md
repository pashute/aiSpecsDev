## Filename: tunes.ai.md
**Version:** 1.0.0

# Tunes AI - Sound Effects for DynamAI

Provides sound notifications for different states in DynamAI workflow.

## Sound Effects

### Success Tune
**Pattern:** ta da da
**Frequencies and durations:**
```powershell
[console]::Beep(349, 400);  # F
[console]::Beep(261, 200);  # C
[console]::Beep(261, 200);  # C
[console]::Beep(293, 400);  # D
[console]::Beep(261, 800);  # C
[console]::Beep(329, 400);  # E
[console]::Beep(349, 800);  # F
```

### Fail Tune
**Pattern:** wa wa wa
**Frequencies and durations:**
```powershell
[console]::Beep(200, 300);  # Low tone
[console]::Beep(200, 300);  # Low tone
[console]::Beep(200, 300);  # Low tone
```

### Warn Tune
**Pattern:** SOS
**Frequencies and durations:**
```powershell
[console]::Beep(400, 200);  # Short
[console]::Beep(400, 200);  # Short
[console]::Beep(400, 200);  # Short
[console]::Beep(400, 400);  # Long
[console]::Beep(400, 400);  # Long
[console]::Beep(400, 400);  # Long
[console]::Beep(400, 200);  # Short
[console]::Beep(400, 200);  # Short
[console]::Beep(400, 200);  # Short
```

## Usage

Call the appropriate tune from DynamAI files:
- Success: After completing a task successfully
- Fail: When an error occurs and task halts
- Warn: When a warning or non-critical issue is detected

## Integration

To integrate into DynamAI files, add the beep commands at appropriate locations:
- End of successful steps: Success tune
- Error handling blocks: Fail tune
- Warning conditions: Warn tune
