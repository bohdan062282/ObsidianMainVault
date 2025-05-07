https://docs.unity3d.com/ScriptReference/Gizmos.html

Gizmos are used to give visual debugging or setup aids in the Scene view.

All gizmo drawing has to be done in either [MonoBehaviour.OnDrawGizmos](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnDrawGizmos.html) or [MonoBehaviour.OnDrawGizmosSelected](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnDrawGizmosSelected.html) functions of the script. [MonoBehaviour.OnDrawGizmos](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnDrawGizmos.html) is called when the Scene view or Game view is repainted. All gizmos that render in [MonoBehaviour.OnDrawGizmos](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnDrawGizmos.html) are pickable. [MonoBehaviour.OnDrawGizmosSelected](https://docs.unity3d.com/ScriptReference/MonoBehaviour.OnDrawGizmosSelected.html) is called only if the object the script is attached to is selected.

##### Example:
`private void OnDrawGizmosSelected()
`{
``    Gizmos.color = Color.blue;
``    Gizmos.DrawWireSphere(transform.position, radius);
`}

