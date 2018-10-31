sql:
select
    b1.country_cn_name as country_name,
    b0.device_name,
    b0.phoneservice_software_ver,
    b0.total_users,
    b0.new_users,
    b0.active_users
from
(
    select
        number_cd,
        upper(device_name) as device_name,
        upper(phoneservice_software_ver) as phoneservice_software_ver,
        total_users,
        new_users,
        active_users
    from
        Dwd_Onl_Phoneservice_User_Statis_Ds
    where
        pt_d = '20170801'
)b0
left outer join
(
    select
        country_number_cd,
        country_cn_name
    from
    biads.ads_phoneservice_mcc_contry_ds
)b1
on b0.number_cd = b1.country_number_cd
解析出的图谱
ActionRoute {
	alias: null,
	tableName: TableName {
		name: ads_phoneservice_mcc_contry_ds
	},
	libraryName: LibraryName {
		name: biads
	},
	columnList: TResultColumnList {
		colList: {
			TResultColumn {
				colName: ColName {
					name: country_number_cd
				},
				tNameOrAlias: null,
				colType: null,
				colComment: null,
				alias: null,
				functionCall: null,
				allColumn: false,
				sourceColumn: null,
				sensitive: 0,
				tArrayExp: null
			},
			TResultColumn {
				colName: ColName {
					name: country_cn_name
				},
				tNameOrAlias: null,
				colType: null,
				colComment: null,
				alias: null,
				functionCall: null,
				allColumn: false,
				sourceColumn: null,
				sensitive: 0,
				tArrayExp: null
			}
		}
	},
	filterColumns: null,
	actionRoute: ActionRoute {
		alias: Alias {
			name: b1
		},
		tableName: null,
		libraryName: null,
		columnList: TResultColumnList {
			colList: {
				TResultColumn {
					colName: ColName {
						name: country_cn_name
					},
					tNameOrAlias: TNameOrAlias {
						name: b1
					},
					colType: null,
					colComment: null,
					alias: Alias {
						name: country_name
					},
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				},
				TResultColumn {
					colName: ColName {
						name: device_name
					},
					tNameOrAlias: TNameOrAlias {
						name: b0
					},
					colType: null,
					colComment: null,
					alias: null,
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				},
				TResultColumn {
					colName: ColName {
						name: phoneservice_software_ver
					},
					tNameOrAlias: TNameOrAlias {
						name: b0
					},
					colType: null,
					colComment: null,
					alias: null,
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				},
				TResultColumn {
					colName: ColName {
						name: total_users
					},
					tNameOrAlias: TNameOrAlias {
						name: b0
					},
					colType: null,
					colComment: null,
					alias: null,
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				},
				TResultColumn {
					colName: ColName {
						name: new_users
					},
					tNameOrAlias: TNameOrAlias {
						name: b0
					},
					colType: null,
					colComment: null,
					alias: null,
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				},
				TResultColumn {
					colName: ColName {
						name: active_users
					},
					tNameOrAlias: TNameOrAlias {
						name: b0
					},
					colType: null,
					colComment: null,
					alias: null,
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				}
			}
		},
		filterColumns: null,
		actionRoute: null,
		lateralViews: null
	},
	lateralViews: null
}
ActionRoute {
	alias: null,
	tableName: TableName {
		name: Dwd_Onl_Phoneservice_User_Statis_Ds
	},
	libraryName: null,
	columnList: TResultColumnList {
		colList: {
			TResultColumn {
				colName: ColName {
					name: number_cd
				},
				tNameOrAlias: null,
				colType: null,
				colComment: null,
				alias: null,
				functionCall: null,
				allColumn: false,
				sourceColumn: null,
				sensitive: 0,
				tArrayExp: null
			},
			TResultColumn {
				colName: null,
				tNameOrAlias: null,
				colType: null,
				colComment: null,
				alias: Alias {
					name: device_name
				},
				functionCall: TFunctionCall {
					name: upper,
					caseWhenClauses: null,
					funParams: TFunParams {
						functionCalls: null,
						resultColumns: {
							TResultColumn {
								colName: ColName {
									name: device_name
								},
								tNameOrAlias: null,
								colType: null,
								colComment: null,
								alias: null,
								functionCall: null,
								allColumn: false,
								sourceColumn: null,
								sensitive: 0,
								tArrayExp: null
							}
						},
						literals: null
					},
					type: null
				},
				allColumn: false,
				sourceColumn: null,
				sensitive: 0,
				tArrayExp: null
			},
			TResultColumn {
				colName: null,
				tNameOrAlias: null,
				colType: null,
				colComment: null,
				alias: Alias {
					name: phoneservice_software_ver
				},
				functionCall: TFunctionCall {
					name: upper,
					caseWhenClauses: null,
					funParams: TFunParams {
						functionCalls: null,
						resultColumns: {
							TResultColumn {
								colName: ColName {
									name: phoneservice_software_ver
								},
								tNameOrAlias: null,
								colType: null,
								colComment: null,
								alias: null,
								functionCall: null,
								allColumn: false,
								sourceColumn: null,
								sensitive: 0,
								tArrayExp: null
							}
						},
						literals: null
					},
					type: null
				},
				allColumn: false,
				sourceColumn: null,
				sensitive: 0,
				tArrayExp: null
			},
			TResultColumn {
				colName: ColName {
					name: total_users
				},
				tNameOrAlias: null,
				colType: null,
				colComment: null,
				alias: null,
				functionCall: null,
				allColumn: false,
				sourceColumn: null,
				sensitive: 0,
				tArrayExp: null
			},
			TResultColumn {
				colName: ColName {
					name: new_users
				},
				tNameOrAlias: null,
				colType: null,
				colComment: null,
				alias: null,
				functionCall: null,
				allColumn: false,
				sourceColumn: null,
				sensitive: 0,
				tArrayExp: null
			},
			TResultColumn {
				colName: ColName {
					name: active_users
				},
				tNameOrAlias: null,
				colType: null,
				colComment: null,
				alias: null,
				functionCall: null,
				allColumn: false,
				sourceColumn: null,
				sensitive: 0,
				tArrayExp: null
			}
		}
	},
	filterColumns: null,
	actionRoute: ActionRoute {
		alias: Alias {
			name: b0
		},
		tableName: null,
		libraryName: null,
		columnList: TResultColumnList {
			colList: {
				TResultColumn {
					colName: ColName {
						name: country_cn_name
					},
					tNameOrAlias: TNameOrAlias {
						name: b1
					},
					colType: null,
					colComment: null,
					alias: Alias {
						name: country_name
					},
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				},
				TResultColumn {
					colName: ColName {
						name: device_name
					},
					tNameOrAlias: TNameOrAlias {
						name: b0
					},
					colType: null,
					colComment: null,
					alias: null,
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				},
				TResultColumn {
					colName: ColName {
						name: phoneservice_software_ver
					},
					tNameOrAlias: TNameOrAlias {
						name: b0
					},
					colType: null,
					colComment: null,
					alias: null,
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				},
				TResultColumn {
					colName: ColName {
						name: total_users
					},
					tNameOrAlias: TNameOrAlias {
						name: b0
					},
					colType: null,
					colComment: null,
					alias: null,
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				},
				TResultColumn {
					colName: ColName {
						name: new_users
					},
					tNameOrAlias: TNameOrAlias {
						name: b0
					},
					colType: null,
					colComment: null,
					alias: null,
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				},
				TResultColumn {
					colName: ColName {
						name: active_users
					},
					tNameOrAlias: TNameOrAlias {
						name: b0
					},
					colType: null,
					colComment: null,
					alias: null,
					functionCall: null,
					allColumn: false,
					sourceColumn: null,
					sensitive: 0,
					tArrayExp: null
				}
			}
		},
		filterColumns: null,
		actionRoute: null,
		lateralViews: null
	},
	lateralViews: null
}
