# 🚀 Guía de Despliegue de Datos - DAOPCREDICORP

Este repositorio contiene los formularios estandarizados para la gestión de pases a producción. El flujo está diseñado para garantizar la trazabilidad, el control de calidad y el cumplimiento de las políticas de gobierno de datos.

## 📋 Flujo de Trabajo (Workflow)

El despliegue se divide en dos niveles jerárquicos:

### 1. Nivel Macro: Issue Padre (HU)
*   **Propósito:** Documentar la justificación de negocio, el impacto y las aprobaciones globales.
*   **Cuándo usarlo:** Al iniciar cualquier nueva funcionalidad, migración o ajuste mayor.
*   **Acción:** Completa el formulario de `Solicitud de Pase (General)`. Este issue debe permanecer abierto durante todo el ciclo de vida del pase.

### 2. Nivel Micro: Subissues (Intentos Técnicos)
*   **Propósito:** Documentar la ejecución técnica, el commit a desplegar y el plan de rollback.
*   **Cuándo usarlo:** Para ejecutar el pase real. Cada subissue representa un **intento único**.
*   **Regla de Reintento:** 
    *   Si el flujo es **rechazado**, el subissue actual será cerrado.
    *   Se deberá crear un nuevo subissue de tipo *Regular* o *Express* según corresponda, siempre vinculado al Issue Padre original.
*   **Tipos de Subissue:**
    *   `Pase Regular`: Para despliegues complejos que requieren validación en entorno de Certificación (UAT).
    *   `Pase Express`: Para parches rápidos o cambios de bajo impacto (despliegue directo a producción).

---

## 🛠️ Instrucciones de uso para el equipo técnico

1.  **Iniciar Pase:** Crea un nuevo Issue usando la plantilla **"Solicitud de Pase (General)"**.
2.  **Vincular:** Una vez aprobado el marco general, el ingeniero responsable debe crear el subissue técnico (Regular o Express) y enlazado a la Issue Padre.
3.  **Auditoría:** Los aprobadores (PO, Seguridad, Data Steward, CL) realizarán sus revisiones dentro del subissue activo.
4.  **Cierre:** 
    *   Un subissue solo se cierra cuando el despliegue es exitoso o cuando es rechazado para dar paso a un reintento.
    *   El Issue Padre se cierra únicamente cuando se han completado satisfactoriamente todos los subissues técnicos asociados.

---

## 🛡️ Roles de Gobierno
Cada pase requiere la validación de los siguientes roles, quienes darán su V°B° en los formularios:
*   **Product Owner:** Validación de valor de negocio.
*   **Data Engineer (CL/Responsable):** Conformidad técnica.
*   **Analista de Seguridad:** Políticas de acceso y masking.
*   **Custodio Técnico:** Calidad de la data post-pase.
*   **Data Steward:** Integridad del catálogo.