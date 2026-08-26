# PTC Mask Transfer System 4-Axis PLC/HMI Design Draft

This folder is the text export of the controlled Excel design draft.
The Excel workbook remains the master file; these Markdown and CSV files make the design readable in GitHub and ChatGPT.

## Scope

- Axis1: X traverse, auto and manual/teach.
- Axis2: X lift, auto and manual/teach, including gripper, vacuum and vacuum release.
- Axis3: Z lift, auto flow for inspection station, barcode and visual inspection.
- Axis4: Z rotation, manual/teach only. Auto flow must not command Axis4 positioning.
- BOM, PDFs, temporary files and confidential customer source files are not committed.

## Exported Sheets

| Sheet | Markdown | CSV | Rows |
| --- | --- | --- | --- |
| 00_設計標準總覽 | [00_design_standard_overview.md](requirements/00_design_standard_overview.md) | [00_design_standard_overview.csv](requirements/00_design_standard_overview.csv) | 10 |
| 01_位址分區標準 | [01_address_range_standard.md](requirements/01_address_range_standard.md) | [01_address_range_standard.csv](requirements/01_address_range_standard.csv) | 28 |
| 02_XY點位表 | [02_xy_io.md](io-list/02_xy_io.md) | [02_xy_io.csv](io-list/02_xy_io.csv) | 62 |
| 03_M共用_HMI_Barcode | [03_m_common_hmi_barcode.md](requirements/03_m_common_hmi_barcode.md) | [03_m_common_hmi_barcode.csv](requirements/03_m_common_hmi_barcode.csv) | 100 |
| 04_M軸1_X橫移 | [04_m_axis1_x_traverse.md](requirements/04_m_axis1_x_traverse.md) | [04_m_axis1_x_traverse.csv](requirements/04_m_axis1_x_traverse.csv) | 24 |
| 05_M軸2_X升降 | [05_m_axis2_x_lift.md](requirements/05_m_axis2_x_lift.md) | [05_m_axis2_x_lift.csv](requirements/05_m_axis2_x_lift.csv) | 38 |
| 06_M軸3_Z升降 | [06_m_axis3_z_lift.md](requirements/06_m_axis3_z_lift.md) | [06_m_axis3_z_lift.csv](requirements/06_m_axis3_z_lift.csv) | 24 |
| 07_M軸4_Z旋轉 | [07_m_axis4_z_rotate.md](requirements/07_m_axis4_z_rotate.md) | [07_m_axis4_z_rotate.csv](requirements/07_m_axis4_z_rotate.csv) | 26 |
| 08_D資料參數 | [08_d_data_parameters.md](requirements/08_d_data_parameters.md) | [08_d_data_parameters.csv](requirements/08_d_data_parameters.csv) | 105 |
| 09_T_S流程分區 | [09_t_s_sequence_ranges.md](sequence/09_t_s_sequence_ranges.md) | [09_t_s_sequence_ranges.csv](sequence/09_t_s_sequence_ranges.csv) | 16 |
| 10_流程_X橫移_S100_S150 | [10_sequence_x_traverse_s100_s150.md](sequence/10_sequence_x_traverse_s100_s150.md) | [10_sequence_x_traverse_s100_s150.csv](sequence/10_sequence_x_traverse_s100_s150.csv) | 29 |
| 11_流程_X升降_S200 | [11_sequence_x_lift_s200.md](sequence/11_sequence_x_lift_s200.md) | [11_sequence_x_lift_s200.csv](sequence/11_sequence_x_lift_s200.csv) | 17 |
| 12_流程_Z升降_Barcode_S300 | [12_sequence_z_lift_barcode_s300.md](sequence/12_sequence_z_lift_barcode_s300.md) | [12_sequence_z_lift_barcode_s300.csv](sequence/12_sequence_z_lift_barcode_s300.csv) | 15 |
| 13_流程_Z旋轉手動_S400 | [13_sequence_z_rotate_manual_s400.md](sequence/13_sequence_z_rotate_manual_s400.md) | [13_sequence_z_rotate_manual_s400.csv](sequence/13_sequence_z_rotate_manual_s400.csv) | 8 |
| 14_HMI畫面標準 | [14_hmi_screen_standard.md](requirements/14_hmi_screen_standard.md) | [14_hmi_screen_standard.csv](requirements/14_hmi_screen_standard.csv) | 21 |
| 15_異常警報標準 | [15_alarm_standard.md](requirements/15_alarm_standard.md) | [15_alarm_standard.csv](requirements/15_alarm_standard.csv) | 32 |
| 16_驗收_Release_Gate | [16_release_gate.md](requirements/16_release_gate.md) | [16_release_gate.csv](requirements/16_release_gate.csv) | 12 |
| 99_來源與版本 | [99_source_and_version.md](requirements/99_source_and_version.md) | [99_source_and_version.csv](requirements/99_source_and_version.csv) | 7 |
| 00_總覽 | [00_legacy_overview.md](requirements/00_legacy_overview.md) | [00_legacy_overview.csv](requirements/00_legacy_overview.csv) | 8 |
| 17_CODEX審查封口 | [17_codex_review_closure.md](requirements/17_codex_review_closure.md) | [17_codex_review_closure.csv](requirements/17_codex_review_closure.csv) | 15 |
| 18_Fault_Output_Matrix | [18_fault_output_matrix.md](requirements/18_fault_output_matrix.md) | [18_fault_output_matrix.csv](requirements/18_fault_output_matrix.csv) | 23 |
| 19_Timeout_參數標準 | [19_timeout_parameter_standard.md](requirements/19_timeout_parameter_standard.md) | [19_timeout_parameter_standard.csv](requirements/19_timeout_parameter_standard.csv) | 8 |
| 20_HMI權限與互鎖 | [20_hmi_permission_interlock.md](requirements/20_hmi_permission_interlock.md) | [20_hmi_permission_interlock.csv](requirements/20_hmi_permission_interlock.csv) | 13 |
| 00_4軸新設計總覽 | [00_4axis_new_design_overview.md](requirements/00_4axis_new_design_overview.md) | [00_4axis_new_design_overview.csv](requirements/00_4axis_new_design_overview.csv) | 11 |
| 01_IO新增與配置 | [01_io_additions.md](io-list/01_io_additions.md) | [01_io_additions.csv](io-list/01_io_additions.csv) | 13 |
| 21_4軸Auto完整流程 | [21_4axis_auto_full_sequence.md](sequence/21_4axis_auto_full_sequence.md) | [21_4axis_auto_full_sequence.csv](sequence/21_4axis_auto_full_sequence.csv) | 22 |
| 22_功能Enable矩陣 | [22_feature_enable_matrix.md](requirements/22_feature_enable_matrix.md) | [22_feature_enable_matrix.csv](requirements/22_feature_enable_matrix.csv) | 7 |
| 23_Barcode_History設計 | [23_barcode_history_design.md](requirements/23_barcode_history_design.md) | [23_barcode_history_design.csv](requirements/23_barcode_history_design.csv) | 8 |
| 24_HMI_4軸畫面 | [24_hmi_4axis_screens.md](requirements/24_hmi_4axis_screens.md) | [24_hmi_4axis_screens.csv](requirements/24_hmi_4axis_screens.csv) | 16 |
| 25_4軸CODEX封口清單 | [25_4axis_codex_closure_checklist.md](requirements/25_4axis_codex_closure_checklist.md) | [25_4axis_codex_closure_checklist.csv](requirements/25_4axis_codex_closure_checklist.csv) | 14 |
| 26_IO不可新增與待確認 | [26_io_fixed_no_extra_pending.md](io-list/26_io_fixed_no_extra_pending.md) | [26_io_fixed_no_extra_pending.csv](io-list/26_io_fixed_no_extra_pending.csv) | 6 |
| 01_IO補充_雙線圈版 | [01_io_dual_coil_supplement.md](io-list/01_io_dual_coil_supplement.md) | [01_io_dual_coil_supplement.csv](io-list/01_io_dual_coil_supplement.csv) | 11 |
| 27_雙線圈控制標準 | [27_dual_coil_control_standard.md](requirements/27_dual_coil_control_standard.md) | [27_dual_coil_control_standard.csv](requirements/27_dual_coil_control_standard.csv) | 5 |
| 28_20260826驗證封口 | [33_28_20260826.md](requirements/33_28_20260826.md) | [33_28_20260826.csv](requirements/33_28_20260826.csv) | 22 |
| 29_全量來源驗證封口 | [34_29.md](requirements/34_29.md) | [34_29.csv](requirements/34_29.csv) | 22 |
