# PROCESOS

## Diagrama de clases (PARAMETRIZACION)

```mermaid
classDiagram
    class PROCEDURES {
        +int id_procedure
        +String consecutive
        +int id_proc_type
        +obtenerProcedimientos()
        +obtenerProcedimiento(id: int)
        +crearProcedimiento()
        +actualizarProcedimiento(id: int)
        +eliminarProcedimiento(id: int)
    }
    class PROCEDURES_TYPES {
        +int id_proc_type
        +String name
        +obtenerTiposDeProcedimiento()
        +obtenerTipoDeProcedimiento(id: int)
        +crearTipoDeProcedimiento()
        +actualizarTipoDeProcedimiento(id: int)
        +eliminarTipoDeProcedimiento(id: int)
    }
    class PROC_TYPES_PHASES {
        +int id_proc_type_phase
        +int id_proc_type
        +int id_phase
        +obtenerTiposDeFase()
        +obtenerTipoDeFase(id: int)
        +crearTipoDeFase()
        +actualizarTipoDeFase(id: int)
        +eliminarTipoDeFase(id: int)
    }
    class ROLES {
        +int id_role
        +String name
        +obtenerRoles()
        +obtenerRol(id: int)
        +crearRol()
        +actualizarRol(id: int)
        +eliminarRol(id: int)
    }
    class STATES {
        +int id_state
        +String name
        +obtenerEstados()
        +obtenerEstado(id: int)
        +crearEstado()
        +actualizarEstado(id: int)
        +eliminarEstado(id: int)
    }
    class JOBS {
        +int id_job
        +String name
        +obtenerTrabajos()
        +obtenerTrabajo(id: int)
        +crearTrabajo()
        +actualizarTrabajo(id: int)
        +eliminarTrabajo(id: int)
    }
    class STATES_JOBS {
        +int id_state_job
        +int id_state
        +int id_job
        +obtenerEstadosTrabajos()
        +obtenerEstadoTrabajo(id: int)
        +crearEstadoTrabajo()
        +actualizarEstadoTrabajo(id: int)
        +eliminarEstadoTrabajo(id: int)
    }
    class PHASES {
        +int id_phase
        +String name
        +int id_state
        +int id_phase_caterogy
        +obtenerFases()
        +obtenerFase(id: int)
        +crearFase()
        +actualizarFase(id: int)
        +eliminarFase(id: int)
    }
    class PHASE_CATEGORY {
        +int id_phase_caterogy
        +String name
        +obtenerCategoriasDeFase()
        +obtenerCategoriaDeFase(id: int)
        +crearCategoriaDeFase()
        +actualizarCategoriaDeFase(id: int)
        +eliminarCategoriaDeFase(id: int)
    }
    class ACTIONS {
        +int id_action
        +String name
        +obtenerAcciones()
        +obtenerAccion(id: int)
        +crearAccion()
        +actualizarAccion(id: int)
        +eliminarAccion(id: int)
    }
    class PHASE_ACTIONS {
        +int id_phase_action
        +int id_phase
        +int id_action
        +obtenerAccionesDeFase()
        +obtenerAccionDeFase(id: int)
        +crearAccionDeFase()
        +actualizarAccionDeFase(id: int)
        +eliminarAccionDeFase(id: int)
    }
    class ROLES_PHASE {
        +int id_ROLE_PHASE
        +int id_phase
        +int id_role
        +obtenerRolesDeFase()
        +obtenerRolDeFase(id: int)
        +crearRolDeFase()
        +actualizarRolDeFase(id: int)
        +eliminarRolDeFase(id: int)
    }
    class PHASES_FLOW {
        +int id_phase_flow
        +int id_phase_from
        +int id_phase_to
        +obtenerFlujoDeFases()
        +obtenerFlujoDeFase(id: int)
        +crearFlujoDeFase()
        +actualizarFlujoDeFase(id: int)
        +eliminarFlujoDeFase(id: int)
    }

    PROCEDURES_TYPES "posee" --> PROCEDURES : id_proc_type
    PROCEDURES_TYPES "asigna" --> PROC_TYPES_PHASES : id_proc_type
    PROC_TYPES_PHASES "incluye" --> PHASES : id_phase
    STATES "define" --> PHASES : id_state
    PHASE_CATEGORY "clasifica" --> PHASES : id_phase_caterogy
    PHASES "tiene" --> PHASE_ACTIONS : id_phase
    ACTIONS "es parte de" --> PHASE_ACTIONS : id_action
    ROLES "es asignado a" --> ROLES_PHASE : id_role
    PHASES "tiene" --> ROLES_PHASE : id_phase
    PHASES "fluye a" --> PHASES_FLOW : id_phase_from
    PHASES "fluye desde" --> PHASES_FLOW : id_phase_to
    JOBS "es gestionado por" --> STATES_JOBS : id_job
    STATES "es gestionado por" --> STATES_JOBS : id_state



```

## Diagrama de clases (REGISTROS)

```mermaid
    classDiagram
    class PROCEDURES {
        +int id_procedure
        +String consecutive
        +int id_proc_type
        +obtenerProcedimientos()
        +obtenerProcedimiento(id: int)
        +crearProcedimiento()
        +actualizarProcedimiento(id: int)
        +eliminarProcedimiento(id: int)
    }
    class PROC_ROLES {
        +int id_proc_role
        +String name
        +obtenerRolesDeProcedimiento()
        +obtenerRolDeProcedimiento(id: int)
        +crearRolDeProcedimiento()
        +actualizarRolDeProcedimiento(id: int)
        +eliminarRolDeProcedimiento(id: int)
    }
    class PROC_STATES {
        +int id_proc_state
        +String name
        +obtenerEstadosDeProcedimiento()
        +obtenerEstadoDeProcedimiento(id: int)
        +crearEstadoDeProcedimiento()
        +actualizarEstadoDeProcedimiento(id: int)
        +eliminarEstadoDeProcedimiento(id: int)
    }
    class PROC_JOBS {
        +int id_proc_job
        +String name
        +obtenerTrabajosDeProcedimiento()
        +obtenerTrabajoDeProcedimiento(id: int)
        +crearTrabajoDeProcedimiento()
        +actualizarTrabajoDeProcedimiento(id: int)
        +eliminarTrabajoDeProcedimiento(id: int)
    }
    class PROC_STATES_JOBS {
        +int id_proc_state_job
        +int id_proc_state
        +int id_proc_job
        +obtenerEstadosTrabajosDeProcedimiento()
        +obtenerEstadoTrabajoDeProcedimiento(id: int)
        +crearEstadoTrabajoDeProcedimiento()
        +actualizarEstadoTrabajoDeProcedimiento(id: int)
        +eliminarEstadoTrabajoDeProcedimiento(id: int)
    }
    class PROC_PHASES {
        +int id_proc_phase
        +String name
        +int id_proc_state
        +int id_proc_phase_caterogy
        +int id_procedure
        +obtenerFasesDeProcedimiento()
        +obtenerFaseDeProcedimiento(id: int)
        +crearFaseDeProcedimiento()
        +actualizarFaseDeProcedimiento(id: int)
        +eliminarFaseDeProcedimiento(id: int)
    }
    class PROC_PHASE_CATEGORY {
        +int id_proc_phase_caterogy
        +String name
        +obtenerCategoriasDeFaseDeProcedimiento()
        +obtenerCategoriaDeFaseDeProcedimiento(id: int)
        +crearCategoriaDeFaseDeProcedimiento()
        +actualizarCategoriaDeFaseDeProcedimiento(id: int)
        +eliminarCategoriaDeFaseDeProcedimiento(id: int)
    }
    class PROC_ACTIONS {
        +int id_proc_action
        +String name
        +obtenerAccionesDeProcedimiento()
        +obtenerAccionDeProcedimiento(id: int)
        +crearAccionDeProcedimiento()
        +actualizarAccionDeProcedimiento(id: int)
        +eliminarAccionDeProcedimiento(id: int)
    }
    class PROC_PHASE_ACTIONS {
        +int id_proc_phase_action
        +int id_proc_phase
        +int id_proc_action
        +obtenerAccionesDeFaseDeProcedimiento()
        +obtenerAccionDeFaseDeProcedimiento(id: int)
        +crearAccionDeFaseDeProcedimiento()
        +actualizarAccionDeFaseDeProcedimiento(id: int)
        +eliminarAccionDeFaseDeProcedimiento(id: int)
    }
    class PROC_ROLES_PHASE {
        +int id_proc_ROLE_PHASE
        +int id_proc_phase
        +int id_proc_role
        +obtenerRolesDeFaseDeProcedimiento()
        +obtenerRolDeFaseDeProcedimiento(id: int)
        +crearRolDeFaseDeProcedimiento()
        +actualizarRolDeFaseDeProcedimiento(id: int)
        +eliminarRolDeFaseDeProcedimiento(id: int)
    }
    class PROC_PHASES_FLOW {
        +int id_proc_phase_flow
        +int id_proc_phase_from
        +int id_proc_phase_to
        +obtenerFlujoDeFasesDeProcedimiento()
        +obtenerFlujoDeFaseDeProcedimiento(id: int)
        +crearFlujoDeFaseDeProcedimiento()
        +actualizarFlujoDeFaseDeProcedimiento(id: int)
        +eliminarFlujoDeFaseDeProcedimiento(id: int)
    }

    PROC_STATES "define" --> PROC_PHASES : id_proc_state
    PROC_PHASE_CATEGORY "clasifica" --> PROC_PHASES : id_proc_phase_caterogy
    PROC_PHASES "tiene" --> PROC_PHASE_ACTIONS : id_proc_phase
    PROC_ACTIONS "es parte de" --> PROC_PHASE_ACTIONS : id_proc_action
    PROC_ROLES "es asignado a" --> PROC_ROLES_PHASE : id_proc_role
    PROC_PHASES "tiene" --> PROC_ROLES_PHASE : id_proc_phase
    PROC_PHASES "fluye a" --> PROC_PHASES_FLOW : id_proc_phase_from
    PROC_PHASES "fluye desde" --> PROC_PHASES_FLOW : id_proc_phase_to
    PROC_JOBS "es gestionado por" --> PROC_STATES_JOBS : id_proc_job
    PROC_STATES "es gestionado por" --> PROC_STATES_JOBS : id_proc_state
    PROCEDURES "define" --> PROC_PHASES : id_procedure

```
